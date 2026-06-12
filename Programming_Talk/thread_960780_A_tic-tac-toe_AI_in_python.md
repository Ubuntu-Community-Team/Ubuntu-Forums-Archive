---
title: "A tic-tac-toe AI in python"
date: 2008-10-27
forum: Programming Talk
---

### Post by MaxIBoy on 2008-10-27
After reading [this](http://ubuntuforums.org/showthread.php?t=958634) thread, I've decided my AI does not belong with that project. It isn't portable to other puzzle games (without some extra work,) and it's not very advanced. Still, this might come in handy for *someone*. It successfully brought every game to a draw.

This isn't a full game engine, just the AI. There's not a real algorithm; instead it uses a "compressed" truth table. It always assumes it's the 'x' player.

```
#TicTacToe AI
#use the function "AI"
#give it a 3-by-3 array of characters (x, o, or space)
# [[' ', ' ', ' '],
#  [' ', ' ', ' '],
#  [' ', ' ', ' ']]
#the function returns the modified board
#the AI assumes that it is the "x" player



            
            
                
def AI(board):

    #game winning code

    
    #complete horizontal sets of 3
    for rowNum in range(3):
        totalOfYours = 0
        openSlot = None
        for cellNum in range(3):
            if board[rowNum][cellNum] == 'x':
                totalOfYours += 1
            elif board[rowNum][cellNum] == ' ':
                openSlot = cellNum
            else: break #row cannot be completed because it's blocked by an enemy
        if openSlot != None and totalOfYours == 2:
            #there is an empty slot which would win the game
            board[rowNum][openSlot] = 'x'
            return board

    #complete vertical sets of 3
    for colNum in range(3):
        totalOfYours = 0
        openSlot = None
        for cellNum in range(3):
            if board[cellNum][colNum] == 'x':
                totalOfYours += 1
            elif board[cellNum][colNum] == ' ':
                openSlot = cellNum
            else: break
        if openSlot != None and totalOfYours == 2:
            board[openSlot][colNum] = 'x'
            return board

    #complete diagonal sets of 3

    #upper left to lower right
    path = [[0, 0], [1, 1], [2, 2]]
    totalOfYours = 0
    openSlot = None
    for cellNum in range(3):
        if board[path[cellNum][0]][path[cellNum][1]] == 'x':
            totalOfYours += 1
        elif board[path[cellNum][0]][path[cellNum][1]] == ' ':
            openSlot = cellNum
        else: break
    if openSlot != None and totalOfYours == 2:
        board[path[openSlot][0]][path[openSlot][1]] = 'x'
        return board

    #upper right to lower left
    path = [[0, 2], [1, 1], [2, 0]]
    totalOfYours = 0
    openSlot = None
    for cellNum in range(3):
        if board[path[cellNum][0]][path[cellNum][1]] == 'x':
            totalOfYours += 1
        elif board[path[cellNum][0]][path[cellNum][1]] == ' ':
            openSlot = cellNum
        else: break
    if openSlot != None and totalOfYours == 2:
        board[path[openSlot][0]][path[openSlot][1]] = 'x'
        return board





    #code to prevent the enemy from winning by blocking their potential wins
    #with your character 

    
    #complete horizontal sets of 3
    for rowNum in range(3):
        totalOfTheirs = 0
        openSlot = None
        for cellNum in range(3):
            if board[rowNum][cellNum] == 'o':
                totalOfTheirs += 1
            elif board[rowNum][cellNum] == ' ':
                openSlot = cellNum
            else: break 
        if openSlot != None and totalOfTheirs == 2:
            #there is an empty slot which would win the game
            board[rowNum][openSlot] = 'x' #so block it
            return board

    #complete vertical sets of 3
    for colNum in range(3):
        totalOfTheirs = 0
        openSlot = None
        for cellNum in range(3):
            if board[cellNum][colNum] == 'o':
                totalOfTheirs += 1
            elif board[cellNum][colNum] == ' ':
                openSlot = cellNum
            else: break
        if openSlot != None and totalOfTheirs == 2:
            board[openSlot][colNum] = 'x'
            return board

    #complete diagonal sets of 3

    #upper left to lower right
    path = [[0, 0], [1, 1], [2, 2]]
    totalOfTheirs = 0
    openSlot = None
    for cellNum in range(3):
        if board[path[cellNum][0]][path[cellNum][1]] == 'o':
            totalOfTheirs += 1
        elif board[path[cellNum][0]][path[cellNum][1]] == ' ':
            openSlot = cellNum
        else: break
    if openSlot != None and totalOfTheirs == 2:
        board[path[openSlot][0]][path[openSlot][1]] = 'x'
        return board

    #upper right to lower left
    path = [[0, 2], [1, 1], [2, 0]]
    totalOfTheirs = 0
    openSlot = None
    for cellNum in range(3):
        if board[path[cellNum][0]][path[cellNum][1]] == 'o':
            totalOfTheirs += 1
        elif board[path[cellNum][0]][path[cellNum][1]] == ' ':
            openSlot = cellNum
        else: break
    if openSlot != None and totalOfTheirs == 2:
        board[path[openSlot][0]][path[openSlot][1]] = 'x'
        return board





    #game starting code

    #ideal starting move
    if board[1][1] == ' ':
        board [1][1] = 'x'
        return board

    #pick a corner if possible, as there are more potential wins from a corner
    #if a corner is already picked by you, this will create a potential win
    path = [[0, 0], [0, 2], [2, 0], [2, 2]]
    for cellNum in range(4):
        if board[path[cellNum][0]][path[cellNum][1]] == ' ':
            board[path[cellNum][0]][path[cellNum][1]] = 'x'
            return board

    #last resort: pick the first open one you see
    for rowNum in range(3):
        for cellNum in range(3):
            if board[rowNum][cellNum] == ' ':
                board[rowNum][cellNum] = 'x'
                return board

```

---

### Post by vincentpistelli on 2011-03-17
I just wrote a tic-tac-toe ai of my own today, it can play as either x or o. However, it is 301 lines of code long(yikes!).  It is a complete program, not just the engine. Here is the code, as a curiosity(not useful for any learning purpose because of its crappiness):

```

#! /usr/bin/env python
#Tic-Tac-Toe AI written in Python
#Declare Variables
#globalize
global o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
#Spaces:
o = "1"
t = "2"
th = "3"
f = "4"
fv = "5"
s = "6"
sv = "7"
e = "8"
n = "9"
#player choice
plch = " "
#computer piece
cmch = " "
#location
loc = " "
#Turn counter
tcnt = 0
#board
board = """%s | %s | %s
---------    
%s | %s | %s    
---------
%s | %s | %s """ %(o,t,th,f,fv,s,sv,e,n)


#get OS features
import os, sys

#subroutines
def startgame():
    global o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
    os.system("clear")
    #redeclare variables
    #Spaces:
    o = "1"
    t = "2"
    th = "3"
    f = "4"
    fv = "5"
    s = "6"
    sv = "7"
    e = "8"
    n = "9"
    #player choice
    plch = " "
    #computer piece
    cmch = " "
    #location
    loc = " "
    #Turn counter
    tcnt = 0
    #board
    board = """%s | %s | %s
---------    
%s | %s | %s    
---------
%s | %s | %s """ %(o,t,th,f,fv,s,sv,e,n)
    print "***************"
    print "*             *"
    print "* Tic Tac Toe *"
    print "*             *"
    print "***************" 
    print " "
    print " "
    plch = raw_input("Do you want to be x or o? ")
    if plch == "x":
        cmch = "o"
        print "You are player x and you go first!"
        usermove()
    elif plch == "o":
        cmch = "x"
        print "You are player o and you go second!"
        compmove()
    else:
        print "You have entered an invalid value! x or o only!"
        a = raw_input()
        os.system("clear")
        startgame()
    return o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
    
def usermove():
    global o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
    board = """%s | %s | %s
---------    
%s | %s | %s    
---------
%s | %s | %s """ %(o,t,th,f,fv,s,sv,e,n)
    print board
    print "You are player %s" % (plch)
    loc = raw_input("Where do you want to place your piece? ")
    if loc == "1":
        o = plch
    elif loc == "2":
        t = plch
    elif loc == "3":
        th = plch
    elif loc == "4":
        f = plch
    elif loc == "5":
        fv = plch
    elif loc == "6":
        s = plch
    elif loc == "7":
        sv = plch
    elif loc == "8":
        e = plch
    elif loc == "9":
        n = plch
    else:
        print "You have entered an incorrect value! Try Again!"
        a = raw_input()
        usermove()
    tcnt = tcnt + 1
    wincheck()
    if tcnt == 9:
        endgame()
    else:
        compmove()
    os.system("clear")
    board = """%s | %s | %s
---------    
%s | %s | %s    
---------
%s | %s | %s """ %(o,t,th,f,fv,s,sv,e,n)
    print board
    return o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
    
def compmove():
    global o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
    os.system("clear")
    #Blocking player
    #Horizontally
    if o == t and th == "3":
        th = cmch
    elif t == th and o == "1":
        o = cmch
    elif o == th and t == "2":
        t = cmch
    #
    elif f == fv and s == "6":
        s = cmch
    elif fv == s and f == "4":
        f = cmch
    elif f == s and fv == "5":
        fv = cmch
    #
    elif sv == e and n == "9":
        n = cmch
    elif e == n and sv == "7":
        sv = cmch
    elif sv == n and e == "8":
        e = cmch
    #Vertically
    elif o == f and sv == "7":
        sv = cmch
    elif f == sv and o == "1":
        o = cmch
    elif o == sv and f == "4":
        f = cmch
    #
    elif t == fv and e == "8":
        e = cmch
    elif fv == e and t == "2":
        t = cmch
    elif t == e and fv == "5":
        fv = cmch
    #
    elif th == s and n == "9":
        n = cmch
    elif s == n and th == "3":
        th = cmch
    elif th == n and s == "6":
        s = cmch
    #Diagonally
    elif o == fv and n == "9":
        n = cmch
    elif fv == n and o == "1":
        o = cmch
    elif o == n and fv == "5":
        fv = cmch
    #
    elif th == fv and sv == "7":
        sv = cmch
    elif fv == sv and th == "3":
        th = cmch
    elif th == sv and fv == "5":
        fv = cmch
    #Move 1, turn 1 or 2
    elif tcnt == 0:
        fv = cmch
    elif tcnt == 1:
        if fv == plch:
            th = cmch
        elif o == plch or t == plch or th == plch or f == plch or s == plch or sv == plch or e == plch or n == plch:
            fv = cmch
    #Doubling for move 3
    elif tcnt == 2:
        if t != plch:
            t = cmch
        elif f != plch:
            f = cmch
    #Doubling for move 4
    elif tcnt == 3:
        if t != plch and t != cmch:
            t = cmch
        elif f != plch and f != cmch:
            f = cmch
        elif e != plch:
            e = cmch
        elif s != plch:
            s = cmch
    #Other moves
    else:
        if o != plch and o != cmch:
            o = cmch
        elif t != plch and t != cmch:
            t = cmch
        elif th != plch and th != cmch:
            th = cmch
        elif f != plch and f != cmch:
            f = cmch
        elif fv != plch and fv != cmch:
            fv = cmch
        elif s != plch and s != cmch:
            s = cmch
        elif sv != plch and sv != cmch:
            sv = cmch
        elif e != plch and e != cmch:
            e = cmch
        elif n != plch and n != cmch:
            n = cmch
    tcnt = tcnt + 1
    wincheck()
    if tcnt == 9:
        endgame()
    else:
        usermove()
    return    o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
    
def wincheck():
    global o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
    yn = " "
    if o == t == th == "x" or f == fv == s == "x" or sv == e == n == "x" or o == f == sv == "x" or t == fv == e == "x" or th == s == n == "x" or o == fv == n == "x" or th == fv == sv == "x":
        os.system("clear")
        board = """%s | %s | %s
---------    
%s | %s | %s    
---------
%s | %s | %s """ %(o,t,th,f,fv,s,sv,e,n)
        print board
        print "Player x won."
        yn = raw_input("Would you like to play again? yes or no: ")
        if yn == "yes":
            startgame()
        elif yn == "no":
            print "Goodbye!"
            a = raw_input()
            sys.exit()
        else:
            print "Invalid Choice! yes or no."
            os.system("clear")
            wincheck()
    elif o == t == th == "o" or f == fv == s == "o" or sv == e == n == "o" or o == f == sv == "o" or t == fv == e == "o" or th == s == n == "o" or o == fv == n == "o" or th == fv == sv == "o":
        print "player o won"
        yn = raw_input("Would you like to play again? yes or no: ")
        if yn == "yes":
            startgame()
        elif yn == "no":
            print "Goodbye!"
            a = raw_input()
            sys.exit()
        else:
            print "Invalid Choice! yes or no."
            os.system("clear")
            wincheck()
    return o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
            
def endgame():
    global o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
    os.system("clear")
    yn = " "
    print "Oh Well! Nobody won!"
    yn = raw_input("Would you like to play again? yes or no: ")
    if yn == "yes":
        startgame()
    elif yn == "no":
        print "Goodbye!"
        a = raw_input()
        sys.exit()
    else:
        print "Invalid Choice! yes or no."
        os.system("clear")
        endgame()
    return    o,t,th,f,fv,s,sv,e,n,plch,cmch,loc,tcnt,board
        
startgame()

```

Quite bad as you can see, but I'm only slightly above beginner in programming ability:neutral:

---

### Post by schauerlich on 2011-03-17
```
    if loc == "1":
        o = plch
    elif loc == "2":
        t = plch
    elif loc == "3":
        th = plch
    elif loc == "4":
        f = plch
    elif loc == "5":
        fv = plch
    elif loc == "6":
        s = plch
    elif loc == "7":
        sv = plch
    elif loc == "8":
        e = plch
    elif loc == "9":
        n = plch
    else:
        print "You have entered an incorrect value! Try Again!"
```

```
    if o == t and th == "3":
        th = cmch
    elif t == th and o == "1":
        o = cmch
    elif o == th and t == "2":
        t = cmch
    #
    elif f == fv and s == "6":
        s = cmch
    elif fv == s and f == "4":
        f = cmch
    elif f == s and fv == "5":
        fv = cmch
    #
    elif sv == e and n == "9":
        n = cmch
    elif e == n and sv == "7":
        sv = cmch
    elif sv == n and e == "8":
        e = cmch
    #Vertically
    elif o == f and sv == "7":
        sv = cmch
    elif f == sv and o == "1":
        o = cmch
    elif o == sv and f == "4":
        f = cmch
    #
    elif t == fv and e == "8":
        e = cmch
    elif fv == e and t == "2":
        t = cmch
    elif t == e and fv == "5":
        fv = cmch
    #
    elif th == s and n == "9":
        n = cmch
    elif s == n and th == "3":
        th = cmch
    elif th == n and s == "6":
        s = cmch
    #Diagonally
    elif o == fv and n == "9":
        n = cmch
    elif fv == n and o == "1":
        o = cmch
    elif o == n and fv == "5":
        fv = cmch
    #
    elif th == fv and sv == "7":
        sv = cmch
    elif fv == sv and th == "3":
        th = cmch
    elif th == sv and fv == "5":
        fv = cmch
    #Move 1, turn 1 or 2
    elif tcnt == 0:
        fv = cmch
    elif tcnt == 1:
        if fv == plch:
            th = cmch
        elif o == plch or t == plch or th == plch or f == plch or s == plch or sv == plch or e == plch or n == plch:
            fv = cmch
    #Doubling for move 3
    elif tcnt == 2:
        if t != plch:
            t = cmch
        elif f != plch:
            f = cmch
    #Doubling for move 4
    elif tcnt == 3:
        if t != plch and t != cmch:
            t = cmch
        elif f != plch and f != cmch:
            f = cmch
        elif e != plch:
            e = cmch
        elif s != plch:
            s = cmch
    #Other moves
    else:
        if o != plch and o != cmch:
            o = cmch
        elif t != plch and t != cmch:
            t = cmch
        elif th != plch and th != cmch:
            th = cmch
        elif f != plch and f != cmch:
            f = cmch
        elif fv != plch and fv != cmch:
            fv = cmch
        elif s != plch and s != cmch:
            s = cmch
        elif sv != plch and sv != cmch:
            sv = cmch
        elif e != plch and e != cmch:
            e = cmch
        elif n != plch and n != cmch:
            n = cmch
```

Agh! You expand every possible input, and manually decide what to do next? Have you not used lists, dictionaries, for loops, etc? This could be SO much simpler if you represented the board with some collection, and iterated over it instead of manually catching every single case! Not only is it tedious, it's error prone and nigh unreadable. What if you forget one case in there somewhere? Good luck catching such an error! Here's a good rule of thumb: if you need more than 4-5 elif's, there's probably a better way to do it.

---

### Post by andrew1992 on 2011-03-18
While I'm sure both of these get the job done, lots can be gained from learning to write concise, elegant code ;)

---

### Post by vincentpistelli on 2011-03-18
I'm fully aware that my code is quite cryptic and much longer than it needs to be.  I'm just starting to get serious into programming though.  All I really know how to do is brute force the problem listing every possible case.  This is the first large program I've really done.:(
However, I will take your criticism with much thankfulness because I plan on re-writing it and maybe giving it a GUI with Tkinter.  :D

---

### Post by andrew1992 on 2011-03-18
> **vincentpistelli said:**
> I'm fully aware that my code is quite cryptic and much longer than it needs to be.  I'm just starting to get serious into programming though.  All I really know how to do is brute force the problem listing every possible case.  This is the first large program I've really done.:(
However, I will take your criticism with much thankfulness because I plan on re-writing it and maybe giving it a GUI with Tkinter.  :D
Excellent! Writing clean, powerful, concise code is something I'm sure you will learn to be quite fond and proud of :)

---

