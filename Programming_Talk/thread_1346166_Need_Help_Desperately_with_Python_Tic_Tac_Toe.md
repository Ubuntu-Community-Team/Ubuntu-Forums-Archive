---
title: "Need Help Desperately with Python Tic Tac Toe"
date: 2009-12-04
forum: Programming Talk
---

### Post by KWDavis on 2009-12-04
Hi guys, my buddy challenged me that I couldn't figure out this code for python if he gave me two days to do it. I am stuck, he gave me a stencil for it and I have tried a few ways to finish the program. I am coming down to the deadline and I was wondering if someone could fill in the few blank spaces of code or at least tell me what I need to do. I know I have to find a way for the user to input the computer to input and to declare a winner. I plan on telling my friend I cheated, but only after I shock him when he sees I did at first. Thanks so much! If you want compensation, it can be provided! Here is the code, I have marked the places where I need help!

#Human Move turn

def Human_Move(board, player):
print 'Your Turn'
#Human Picks Move
Human_Move = input ('What Space Do You Want(1-9): ')


#NEED HELP HERE!#

return board

#Computr_Move
def Computer_Move(board, player):
print 'Computer\'s Turn', player

#NEED HELP HERE!# 

return board

#GameOver

def Game_Over(board):

#NEED HELP HERE!!!!!#



#Print_Board
def Print_Board(board):
#Loop over each row
for row in [2,1,0]:
print '',
#Loop over each column
for col in range(3):
if col < 2:
print board[row*3 + col] + ' |',
else:
print board[row*3 + col]
#Print divider
if row > 0:
print '---+---+---'

# code runs game, uses the menu main game loop
import random
#Initial menu
print '''Menu:
1 - Human vs. Human
2 - Human vs. Computer
3 - Exit'''
menu_choice = input('Your Choice: ')

#Game loop, goes til exit
while not menu_choice == 3:
board = ['1', '2', '3', '4', '5', '6', '7', '8', '9']
player = 'X'
random.seed()

#Print initial board
Print_Board(board)
#Main loop, continues until game is finished
while not Game_Over(board):
if player == 'X':
board = Human_Move(board, player)
player = 'O'
else:
if menu_choice == 1:
board = Human_Move(board, player)
else:
board = Computer_Move(board, player)

player = 'X'

Print_Board(board)
print '''Menu:
1 - Human vs. Human
2 - Human vs. Computer
3 - Exit'''
menu_choice = input('Your Choice: ')

---

### Post by wmcbrine on 2009-12-04
Please use "code" tags around your code to preserve the indentation. (Some people prefer to use the "php" tag, because it does syntax highlighting. But to me, it looks weird to have a block labelled "PHP" with Python code in it.)

However, there isn't much to look at here. What you're calling "missing pieces" are basically the whole program.

There are lots of Tic-Tac-Toe programs out there whose source you could study. Just Googling "tic tac toe python" will get you some.

---

### Post by nvteighen on 2009-12-05
Look at PycTacToe at my sig... :P

EDIT: I don't mind you "steal" the code, after all it's under the GPLv3 for a reason and some parts aren't even written by me :p, but I suggest you better read the comments and try to understand the code.

---

### Post by KWDavis on 2009-12-05
Hey Guys, Thanks for the tips! I realy appreciate it. i am actually getting it... kinda.

---

