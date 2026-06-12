---
title: "(PYTHON) Trouble with minesweeper"
date: 2014-04-14
forum: Programming Talk
---

### Post by Fusionthefox on 2014-04-14
Right now I am trying to get a 2D array(list of lists) into my minesweeper program in Python. However when I run it, it gives me a "IndexError: list index out of range" error whenever I try to place/flag a bomb. Here is my code I have so far.

```

import string
import os
import random
def check_neighbours(index, board, bombs):
    
    #get the last digit in the index to check for left or right column positions
    if index > 9:
        strindex = str(index)
        second = strindex[1]
    else:
        second = 'a'
    
    if index == 0:  #top left corner
        offsets=[1,10,11]
    elif index == 9:    #top right corner
        offsets =[-1,9,10]
    elif index == 90:   #bottom left corner
        offsets = [-10,-9, 1]
    elif index ==99:    #bottom right corner
        offsets=[-11,-10,-1]
    elif index > 0 and index < 9: #top row 
        offsets = [-1,1,9,10,11]
    elif index >90 and index < 99:  #bottom row
        offsets = [-1,1,-9,-10,-11]
    elif second == '9':     #Right side column
        offsets=[-11,-10,-1,9,10]
    elif second == '0':     #Left side column
        offsets = [-10,-9,1,10,11]
        
    else:
        offsets=[-11,-10,-9,-1,1,9,10,11]
    bombcount = 0;
    for i in offsets:   #check for bombs in all neighbour positions
        if index+i in bombs:
            bombcount+=1
        
    board[index] = bombcount #copy the number of neighbouring bombs
    if bombcount == 0:
        board[index] = ' '
        for i in offsets:   #Recursive function call for all neighbours
            if board[index + i] == '*':
                check_neighbours(index+i, board, bombs)
        

    else:
        return
def print_board(board):
    os.system("cls")
    #Uncomment the above when playing from the DOS-Prompt
board = []
bombs = []
for i in range(10):
    board.append([])
    for j in range(10):
        board[i].append('*')

for i in range(10):
    for j in range(10):
        print("|", board[i][j], end=" ")
    print("|")






def print_reveal(board, bombs):
    count = 0
    
    rowcount = 0
    for i in board:
        if count in bombs:
            i = 'B'
        print("| ", i, end=" ")
        if rowcount == 9:
            print("|")
            rowcount = 0
        else:
            rowcount += 1
        count += 1
board = []
bombs = []
for i in range(10):

    
    loc = random.randint(0, 99)
    while loc in bombs:
        loc = random.randint(0, 99)
    #board[loc] = 'B'
    bombs.append(loc)
    



gameon=True
while(gameon):

    choice = input("Do you want to pick a spot or flag a bomb? (pick or flag)")
    if choice == 'flag':
        bombloc = int(input("Enter your guess for a bomb location: "))
        if bombloc >= 0 and bombloc < 100:
            if board[bombloc] != '*':
                print("already chosen!")
            else:
                board[bombloc] = 'F'
                
        
        
    else:
       
        reveal = int(input("Enter your guess for an open spot: "))
        if reveal >= 0 and reveal < 100:
            if board[reveal] != '*' and board[reveal] != 'F':
                print("already chosen!")
            elif reveal in bombs:
                print("BOOOM!!!")
                gameon = False
            else:
                check_neighbours(reveal,board,bombs)

            
                    
    if '*' not in board:
        print("You WIN!")
        gameon = False
            
    if(gameon):
        print_board(board)
        
    else:
        print_reveal(board,bombs)
    print(bombs)

```
I don't know what to do to fix this issue :( 

I would really appreciate help on this :(

---

### Post by ofnuts on 2014-04-14
1) if you don't know yet where the problem is, insert a few print statements in your code to determine where this happens (after the last that prints and before the one that doesn't)

2) moving the print statements you should be able to narrow down to the culprit line.

3) at that point print the index and the length of the list and it should be obvious.

---

### Post by Fusionthefox on 2014-04-14
Thanks. But this is what roughly happens.

> | * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
| * | * | * | * | * | * | * | * | * | * |
Do you want to pick a spot or flag a bomb? (pick or flag)20
Enter your guess for an open spot: 20
Traceback (most recent call last):
  File "G:\MINESWEEPER2.py", line 114, in <module>
    if board[reveal] != '*' and board[reveal] != 'F':
IndexError: list index out of range

---

### Post by ofnuts on 2014-04-15
And what says:
```

 print len(board), reveal

```

I also note that you are using a one-dimension board[] while it has two dimensions elsewhere.

---

### Post by Fusionthefox on 2014-04-15
How would I be able to make a two dimension board for board[]?

---

### Post by ofnuts on 2014-04-15
When you write "board[i][j]" you are handling your board as a two-dimensional array.

---

### Post by Fusionthefox on 2014-04-15
So something like this?

import string
import os
import random
def check_neighbours(index, board, bombs):
    
    #get the last digit in the index to check for left or right column positions
    if index > 9:
        strindex = str(index)
        second = strindex[1]
    else:
        second = 'a'
    
    if index == 0:  #top left corner
        offsets=[1,10,11]
    elif index == 9:    #top right corner
        offsets =[-1,9,10]
    elif index == 90:   #bottom left corner
        offsets = [-10,-9, 1]
    elif index ==99:    #bottom right corner
        offsets=[-11,-10,-1]
    elif index > 0 and index < 9: #top row 
        offsets = [-1,1,9,10,11]
    elif index >90 and index < 99:  #bottom row
        offsets = [-1,1,-9,-10,-11]
    elif second == '9':     #Right side column
        offsets=[-11,-10,-1,9,10]
    elif second == '0':     #Left side column
        offsets = [-10,-9,1,10,11]
        
    else:
        offsets=[-11,-10,-9,-1,1,9,10,11]
    bombcount = 0;
    for i in offsets:   #check for bombs in all neighbour positions
        if index+i in bombs:
            bombcount+=1
        
    board[index] = bombcount #copy the number of neighbouring bombs
    if bombcount == 0:
        board[index] = ' '
        for i in offsets:   #Recursive function call for all neighbours
            if board[index + i] == '*':
                check_neighbours(index+i, board, bombs)
        

    else:
        return
def print_board(board):
    os.system("cls")
    #Uncomment the above when playing from the DOS-Prompt
board = []
bombs = []
for i in range(10):
    board.append([])
    for j in range(10):
        board[i].append('*')

for i in range(10):
    for j in range(10):
        print("|", board[i][j], end=" ")
    print("|")






def print_reveal(board, bombs):
    count = 0
    
    rowcount = 0
    for i in board:
        if count in bombs:
            i = 'B'
        print("| ", i, end=" ")
        if rowcount == 9:
            print("|")
            rowcount = 0
        else:
            rowcount += 1
        count += 1
board = []
bombs = []
for i in range(10):

    
    loc = random.randint(0, 99)
    while loc in bombs:
        loc = random.randint(0, 99)
    #board[loc] = 'B'
    bombs.append(loc)
    



gameon=True
while(gameon):

    choice = input("Do you want to pick a spot or flag a bomb? (pick or flag)")
    if choice == 'flag':
        bombloc = int(input("Enter your guess for a bomb location: "))
        if bombloc >= 0 and bombloc < 100:
            if board[bombloc] != '*':
                print("already chosen!")
            else:
                board[bombloc] = 'F'
                
        
        
    else:
       
        reveal = int(input("Enter your guess for an open spot: "))
        print (len(board), reveal)
        
        print(len(board),index)
        if reveal >= 0 and reveal < 100:
            if board[reveal] != '*' and board[reveal] != 'F':
                print("already chosen!")
                
            elif reveal in bombs:
                print("BOOOM!!!")
                gameon = False
            else:
                check_neighbours(reveal,board,bombs)

            
                    
    if '*' not in board:
        print("You WIN!")
        gameon = False
            
    if(gameon):
        print_board(board)
        
    else:
        print_reveal(board,bombs)
    print(bombs)

---

