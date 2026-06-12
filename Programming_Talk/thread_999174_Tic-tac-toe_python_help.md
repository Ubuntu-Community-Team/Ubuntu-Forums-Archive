---
title: "Tic-tac-toe python help"
date: 2008-12-01
forum: Programming Talk
---

### Post by SaIva on 2008-12-01
Hi, I wrote a simple tic-tac-toe game in python but it is not working right. I think everything is okay other than my evaluation function, get_val. It always just returns 1 to my get_AI_move function but I'm not sure why. I thought it looked okay when I went over it. Can someone please take a look?

```
#Tic-tac-toe game, human vs. computer. Human always plays first.
#I use a list of nine numbers to represent the board
#0 is "O", the human player.
#1 is "X", the computer player.
#2 just represents an empty square.
#
#Indexes of the numbers in the list represent the board like so:
#0|1|2
#3|4|5
#6|7|8
#
#Where the numbers are the index position


def draw_board(boardPos):
    #This function draws the board.
    #No return values.
    
    i = 0
    while i < 9:
        if boardPos[i] == 0:
            print "O",
        elif boardPos[i] == 1:
            print "X",
        else:
            print " ",
        if (i + 1) % 3 == 0:
            print ""
        else:
            print "|",
        i += 1

def is_empty(boardPos, square_num):
    #This function checks if the square (from 0 to 8) on
    #the given board is empty.
    #Returns true or false.
                                    
    if boardPos[square_num] == 2:
        return True
    return False

def who_won(boardPos):
    #This function checks to see who won on a given board.
    #Returns 0 for human, 1 for computer, 2 for nobody or
    #undetermined.
    
    #Check rows
    if boardPos[0] != 2 and boardPos[0] == boardPos[1] == boardPos[2]:
        return boardPos[0]
    if boardPos[3] != 2 and boardPos[3] == boardPos[4] == boardPos[5]:
        return boardPos[3]
    if boardPos[6] != 2 and boardPos[6] == boardPos[7] == boardPos[8]:
        return boardPos[6]
    #Check columns
    if boardPos[0] != 2 and boardPos[0] == boardPos[3] == boardPos[6]:
        return boardPos[0]
    if boardPos[1] != 2 and boardPos[1] == boardPos[4] == boardPos[7]:
        return boardPos[1]
    if boardPos[2] != 2 and boardPos[2] == boardPos[5] == boardPos[8]:
        return boardPos[2]
    #Check diagonals
    if boardPos[0] != 2 and boardPos[0] == boardPos[4] == boardPos[8]:
        return boardPos[0]
    if boardPos[2] != 2 and boardPos[2] == boardPos[4] == boardPos[6]:
        return boardPos[2]
    return 2;

def get_val(copiedPos, player, boardPos = None):
    #This function finds and returns the value of a board position.
    #Returns -1 if the computer wins, 1 for human, and 0 for a tie.
                                                
    boardPos = copiedPos[:]
    #Make a copy of the original list.
    if who_won(boardPos) == 1:
        return -1
        #Return computer win.
    elif who_won(boardPos) == 0:
        return 1
        #Return human win.
    no_valid_moves = True
    #Variable to check if there are no valid moves left.
    best_val = None
    i = 0
    while i < 9:
        if is_empty(boardPos, i):
            no_valid_moves = False
            if player == -1:
                boardPos[i] = 0
                eval_val = get_val(boardPos, 1)
                if best_val == None:
                    best_val = eval_val
                elif eval_val > best_val:
                    best_val = eval_val
            #If it was the computer's turn, then now try to maximize
            #value for human player.
            else:
                boardPos[i] = -1
                eval_val = get_val(boardPos, -1)
                if best_val == None:
                    best_val = eval_val
                elif eval_val < best_val:
                    best_val = eval_val
            #If it was the human's turn, then now try to minimize
            #value for computer player.
        i += 1
    if no_valid_moves:
        return 0
        #Return end of game with no winner.
    return best_val
    #Return the best value.
        

def get_AI_move(copiedPos, boardPos = None):
    #Finds the computer's best move for a given board position.
    #Returns a number from 0-8.
    
    boardPos = copiedPos[:]
    #Make a copy of the original list.
    best_move = None
    best_move_val = 3
    #Assign a value higher than any possible initially since
    #it will try to find the minimum value now.
    
    i = 0
    while i < 9:
        if is_empty(boardPos, i):
            boardPos[i] = 1
            eval_val = get_val(boardPos, -1)
            if eval_val < best_move_val:
                best_move = i
                best_move_val = eval_val
            boardPos[i] = 2
        i += 1
    #I go through all of the possible moves and try to find the
    #one that has the lowest value and return it.
    return best_move
                
            

print "Tic-tac-toe <3<3<3"

boardPos = [2,2,2,2,2,2,2,2,2]

i = 0
while i < 5:
    #I chose 5 iterations since then the human can go a maximum of five
    #turns and the game ends.
    draw_board(boardPos)
    #First draw the board
    waiting_user = True
    while waiting_user:
        square = int(raw_input("What square do you wish to play in? ")) - 1
        if 0 <= square < 10 and is_empty(boardPos, square):
            boardPos[square] = 0
            waiting_user = False
        else:
            print "Hey bub! That's not a valid input, try again!"
    #Check if the input is valid and square is empty
            
    if who_won(boardPos) == 0:
        print "Whoooo!! You won!!"
        break
    #Check if the human won the game.

    if i == 4:
        print "Looks like a tie!"
    #If it's the fifth iteration, nobody won yet, and the human already went,
    #the game is a tie.

    boardPos[get_AI_move(boardPos)] = 1
    if who_won(boardPos) == 1:
        print "Oh no! You lost!"
        break
    i += 1

```

---

