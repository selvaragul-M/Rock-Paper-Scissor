from tkinter import *
import random

def play():
    global round_count, wins, losses, ties

    if round_count > 10:
        return

    comp_choice = random.choice(['rock', 'paper', 'scissors'])
    user = user_choice.get()
    result = determine_winner(user, comp_choice)

    result_text.delete(1.0, END)
    result_text.insert(END, f"Round {round_count}: {result}\n")
    round_count += 1

    if round_count == 11:
        display_final_result()
        disable_buttons()

def determine_winner(user, comp):
    global wins, losses, ties

    if user == comp:
        ties += 1
        return "It's a tie!"
    elif (user == 'rock' and comp == 'scissors') or (user == 'paper' and comp == 'rock') or (user == 'scissors' and comp == 'paper'):
        wins += 1
        return "You win!"
    else:
        losses += 1
        return "You lose!"

def display_final_result():
    final_result = f"\nFinal Result:\nWins: {wins}\nLosses: {losses}\nTies: {ties}\n\n"
    if wins > losses:
        final_result += "Congratulations!!!, you win overall!"
    elif losses > wins:
        final_result += "Computer wins overall :("
    else:
        final_result += "It's a tie overall!"
    result_text.insert(END, final_result)

def set_choice(choice):
    user_choice.set(choice)
    play()

def reset():
    result_text.delete(1.0, END)
    user_choice.set("")
    global round_count, wins, losses, ties
    round_count = 1
    wins = losses = ties = 0
    enable_buttons()

def enable_buttons():
    for widget in button_frame.winfo_children():
        widget['state'] = 'normal'

def disable_buttons():
    for widget in button_frame.winfo_children():
        widget['state'] = 'disabled'

def exit_game():
    root.destroy()

root = Tk()
root.geometry("400x450")
root.title("Rock, Paper, Scissors")
root.configure(bg='#f0f0f0')

user_choice = StringVar()
round_count = 1
wins = losses = ties = 0

button_frame = Frame(root, bg='#f0f0f0')
button_frame.pack(pady=20)

Button(button_frame, text="Rock", font='arial 13 bold', padx=10, pady=5, bg='#007bff', fg='white', command=lambda: set_choice('rock')).grid(row=0, column=0, padx=10)
Button(button_frame, text="Paper", font='arial 13 bold', padx=10, pady=5, bg='#28a745', fg='white', command=lambda: set_choice('paper')).grid(row=0, column=1, padx=10)
Button(button_frame, text="Scissors", font='arial 13 bold', padx=10, pady=5, bg='#dc3545', fg='white', command=lambda: set_choice('scissors')).grid(row=0, column=2, padx=10)

Label(root, text='Rock, Paper, Scissors', font='arial 20 bold', bg='seashell2').pack(pady=20)

result_text = Text(root, font='arial 10 bold', bg='white', width=50, height=8)
result_text.pack(pady=10)

Button(root, text="Reset", font='arial 13 bold', padx=10, pady=5, bg='#ffc107', fg='black', command=reset).pack(pady=10)
Button(root, text="Exit", font='arial 13 bold', padx=10, pady=5, bg='#dc3545', fg='white', command=exit_game).pack(pady=10)

root.mainloop()


