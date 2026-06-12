---
title: "0's and X's, Python. Trouble with interface"
date: 2007-09-28
forum: Programming Talk
---

### Post by Darkness3477 on 2007-09-28
HI, I'm just trying to throw together a quick and dirty Naughts and Crosses game (tic, tac, toe or whatever you want to tall it) and I've written up the psuedo code for the actual program, however I'm not sure how I should do two things:
1) Store whether or not a field has been marked (with a 0 or X)

2) How to display this on the screen. So far I'm just doing it on the console, I might implement it in gtk or Pygame or whatever in the future. 

The way in which I'm going to be doing the selecting what box you want to mark,  is just have them numbered. 



This is pretty much a simple version of what I was thinking, but I'm just not sure how I want to do it.
```

_1_|_2_|_3_|
_4_|_5_|_6_|
_7_|_8_|_9_|

```

So, some pointers ans possible help on this would be much appreciated. 

Also, as soon as I've got this done and the rest of the program actually written up, I'm going to try some simple AI, so I might be back asking for some more help.

---

### Post by jfinkels on 2007-09-28
> **Darkness3477 said:**
> HI, I'm just trying to throw together a quick and dirty Naughts and Crosses game (tic, tac, toe or whatever you want to tall it) and I've written up the psuedo code for the actual program, however I'm not sure how I should do two things:
1) Store whether or not a field has been marked (with a 0 or X)

2) How to display this on the screen. So far I'm just doing it on the console, I might implement it in gtk or Pygame or whatever in the future. 

The way in which I'm going to be doing the selecting what box you want to mark,  is just have them numbered. 



This is pretty much a simple version of what I was thinking, but I'm just not sure how I want to do it.
```

_1_|_2_|_3_|
_4_|_5_|_6_|
_7_|_8_|_9_|

```

So, some pointers ans possible help on this would be much appreciated. 

Also, as soon as I've got this done and the rest of the program actually written up, I'm going to try some simple AI, so I might be back asking for some more help.

Hi!

Here's a very simple structure for what the game might look like. I hope you like it :D
```
                                                   
table = [[' ', ' ', ' '], \
         [' ', ' ', ' '], \
         [' ', ' ', ' ']]
turn = 'x'
gameover = False

while not gameover:
    choice = 0
    while choice < 1 or choice > 9:
        choice = input('Choose a location (1-9)')
    row = (choice - 1) / 3
    col = (choice % 3) - 1
    if table[row][col] == ' ':
        table[row][col] = turn
        if turn == 'x':
            turn = 'o'
        else:
            turn = 'x'

    print table

    gameover = True
    for row in table:
        for el in row:
            if el == ' ':
                gameover = False

print 'Thanks for playing!'

```

---

### Post by Darkness3477 on 2007-09-28
EDITED:
Thanks for the code, It's pretty helpful and quite similar to how I planned out my program. Whether or not I end up doing it that way is another thing.

Ok, I've advanced some since my last edit of this post, and have come across a few different problems in the way I wanted to implement the interface, but oh well. I've settled on this way and am sticking to it until I make the jump and make a GUI. 

Anyway, the code so far looks like this.... still somewhat unorgasnised and messy looking
```

import random

def squares(i):
    print turn
    if i >= 0 and i <= 3:
        boards[0][i - 1] = "|_X_|"
        print boards


        
#Initialisation of the game board and variables
def init():
    boards = [ [''] * 3 for i in range(3) ]#Creates a 3*3 array
    turn = random.randrange(1,3,1)#Picks who goes first. 1 = X's 2 = 0's
    if turn == 1:
        p1 = "X"
    else:
        p1 = "0"

    for i in range(3):
        boards[0][i] = i+1
    for i in range(3):
        boards[1][i] = i + 4
    for i in range(3):
        boards[2][i] = i + 7
init()        
print "Hi, and welcome to Maver's fantastic Tic Tac Toe game"
print "Type in a number that corresponds to the table below when it is your turn"
print "This game, the person using ", p1, "'s will be starting."
print boards[0]
print boards[1]
print boards[2]


x_turn = input("Please enter the number where you want to place the X: ")
squares(x_turn)


```

So, I've got it set up to randomly pick a random player to go first and what not, but havn't implemented it yet. I just thought I would test it out, and I got a problem. So, i'm kinda annoyed. 
What happens is this: If I enter a 2 at the imput prompt (meaning a I want to place an x in the middle collum, first row or board[0,1]) instead of just changing the value of [0,1] from '2' to 'X' it changed all [0,0] to [0,2] to 'X's Obviously this isn't what I want. Can you gives lend a bit of hand with this?

---

### Post by pmasiar on 2007-09-28
To store gaming field, you can use dictionary where keys are tupples: 
board = dict()
board[1,2] = 'X'

Wiki in my sig has links to more training tasks, I recommend PythonChallenge

---

### Post by Darkness3477 on 2007-09-28
Thanks very much for the heads up with the Dictionary's. I'll look into them, but as far as I can forsee, the 2dimensional Array will be fine for what I want. 

This project really is only for a bit of fun, as I notice it on a lot of 'challenge' websites and see it often used as a beginning project for AI, a field which has interested me for awhile. 

Also, thanks for suggesting you Wiki and PythonChallenge, I've actually looked at both. Python Challenge I didn't really enjoy, and I'm not sure if you Wiki would help, as I know how to program(Although, I'd only say to a basic level) and I really only need to reveiw a lot of Python stuff as it's been a long time since I've used it. 

But, of course, i'll have a look at your Wiki. I haven't seen it for awhile, so there may be some new stuff.

Thanks for the post!

P.S. It's good, I come home and there is a nice fresh post, 4 minutes before my arival!

---

### Post by jfinkels on 2007-09-28
I tried your program, but there still seems to be a few problems (errors), mostly about variables being used outside of the scope in which they were defined (make sure you define global variables outside the scope of functions!). I was unable to recreate the problem you described, though. Here's some other advice (feel free to ignore me completely, it's your program):

Here
```

    for i in range(3):
        boards[0][i] = i+1
    for i in range(3):
        boards[1][i] = i + 4
    for i in range(3):
        boards[2][i] = i + 7

```
You are defining list elements as integers, but here:
```

def squares(i):
    print turn
    if i >= 0 and i <= 3:
        boards[0][i - 1] = "|_X_|"
        print boards

```
You are defining them as strings. I suggest doing something like this for the sake of consistency:
```

# define the empty table (like you did)
boards = [ [''] * 3 for i in range(3) ]
# or if you want to define them with numbers, do
#boards = [[str(3*i + j+ 1) for j in range(3)] for i in range(3)
# then when you set the marker
turn ='X'
choice = input('Choose a number (1-9): ')
boards[(choice - 1) / 3][(choice % 3) -1] = turn

```

---

