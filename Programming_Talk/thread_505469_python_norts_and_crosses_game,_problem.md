---
title: "python norts and crosses game, problem"
date: 2007-07-20
forum: Programming Talk
---

### Post by hessiess on 2007-07-20
im new to programming, lerning python. trying to make a 0 and crosses game, but it dusent work.

curently when the player puts a 0 or cross in, it changes all the lines of the table, insted of just the one thats salected

what am i dooing wrong?

code:

```
game = []
addd = []
nline = []
d=1
run = 2
x = 1
player = '1'


while run > 1:
    player1 = raw_input('player 1')
    player2 = raw_input('player 2')
    
    while x > 0:
        x = 1
        sise = int(raw_input('sise?'))
        if sise < 3:
            print 'to small! _>3'
        elif sise > 2:
            x = 0

    for fg in range(0,sise):
        addd.append('0')

    for f in range(0,sise):
        game.append(addd)

    
    for line in game:
            print line
            print

    if player == '1':
        print player1
    elif player =='2':
        print player2
    
    placex = input('place x?')   
    
    placey = input('place y?')


    placex = placex - 1
    placey = placey - 1
    

    
    game [0][1]
    nline = game[placey]
    del nline[placex]

    print game+['1']
    print
    
    if player == '1':
        nline.insert(placex,'X')
        print nline

    if player == '2':
        nline.insert(placex,'O')
        print nline

    print game+['2']
    print

    del game[placey]
    print game+['3']
    print

    game.insert(placey, nline)

    for line in game:
            print line
            print


    run = 0

    

```

ps, its not comented becose i cannot type a hash with this keybord, the hash button makes a \!

---

### Post by pmasiar on 2007-07-20
Some problems I found:

- you seems to regenerate game (asking for size of the board) in each turn. Do it outside of main game loop
- your main loop is way too long. Try to define some functions doing stuff (and give them good names) to simplify your code. Good rule of thumb is, 15-20, max 30 lines for a function.
- Try to think about better names for variables. 'game' is good: gameboard. But nline? addd? good names help *you* to understand what your code is doing (and what it is doing wrong)
- Your game is list of lists. You don't have to delete and insert  new items, just replace them: game[x][y] = 'O' 

You may want to start with simpler game, like "guess the number". Wiki in my sig has plenty of links.

---

### Post by hessiess on 2007-07-20
thank you:)

i know about the tuns problem.
tryed using functions but thay dident work propaly:(
 
i dedent know you could do game[x][y] = 'O', witch would make most of the variables useless anyway:lolflag:

---

### Post by hessiess on 2007-07-20
still dus the same thing:(

```
player 1a
player 2b
sise?3
['0', '0', '0']

['0', '0', '0']

['0', '0', '0']

a
place x?1
place y?3

['x', '0', '0']

['x', '0', '0']

['x', '0', '0']

_________________________________________________
 gameline
['x', '0', '0']
 why is it changing gameline vairable? it should only change the game list!
```

and the new code

```
game = []
gameline = []

d=1
run = 2
x = 1
player = '1'


while run > 1:
    player1 = raw_input('player 1')
    player2 = raw_input('player 2')
    
    while x > 0:
        x = 1
        sise = int(raw_input('sise?'))
        if sise < 3:
            print 'to small! _>3'
        elif sise > 2:
            x = 0

    for fg in range(0,sise):
        gameline.append('0')

    for f in range(0,sise):
        game.append(gameline)

    
    for line in game:
            print line
            print

    if player == '1':
        print player1
    elif player =='2':
        print player2
    









    placex = input('place x?')   
    
    placey = input('place y?')


    placex = placex - 1
    placey = placey - 1
    

    print
    
    if player == '1':
        game[placey][placex] = 'x'

    elif player == '2':
        game[placey][placex] = 'O'
        print nline

    
    for line in game:
            print line
            print

    print'_________________________________________________'
    print ' gameline'
    print gameline
    print ' why is it changing gameline vairable? it should only change the game list!'

    run = 0

    

```

---

### Post by Smygis on 2007-07-20
Python lists works on reference.

By appending gameline to game, What you realy are doing is appending a reference to gameline in game.

consider the folowing:
```

>>> line = [0,0,0]
>>> otherline = line
>>> otherline[1] = 666
>>> print line
[0, 666, 0]
>>> print otherline
[0, 666, 0]
>>> 
>>> 
>>> line = [0,0,0]
>>> otherline = line[:]
>>> otherline[1] = 666
>>> print line
[0, 0, 0]
>>> print otherline
[0, 666, 0]
>>> 

```

---

### Post by hessiess on 2007-07-21
rewrote the section that makes the table, now it works! thanks to the people who helped me

```
game = []
gameon=1
d=1
run = 2
x = 1
player = 1
a=2

while run > 1:
    player1 = raw_input('player 1')
    player2 = raw_input('player 2')
    
    while x > 0:
        x = 1
        sise = int(raw_input('sise?'))
        if sise < 3:
            print 'to small! _>3'
        elif sise > 2:
            x = 0

    for fg in range(0,sise):
        game.append(['?'])

  
    for x in range(0,sise-1):
        for fh in range(0,sise):
            game[fh] = game[fh]+['?']

    
    for line in game:
            print line
            print

    while gameon>0:
        if player == 1:
            print player1
        elif player == 2:
            print player2

        while a > 0:
            placex = input('place x?')   
            
            placey = input('place y?')

            if game[placey-1][placex-1] =='x':
                print 'used!'
            elif game[placey-1][placex-1] == '?':
                a=0


        placex = placex - 1
        placey = placey - 1
        

        print
        
        if player == 1:
            game[placey][placex] = 'x'

        elif player == 2:
            game[placey][placex] = 'O'
            

        
        for line in game:
            print line
            print
        if player == 1:
            player = 2
        elif player == 2:
            player = 1


    run = 0

    
    if game[placey][placex] == 'x'or'O':
        print 'used!'

```

---

### Post by hessiess on 2007-07-29
its finished! and it detects who wins.

```
game = []
gameon = 1
d = 1
run = 2
x = 1
player = 1
qd = 1
#### vairables for check
test = 1
reed=[]

def checkreed():
    global test
    global gameon

    test = reed.count('x')
    if test == sise:
        print
        print 'yay! '+player1
        print
        gameon = 0
    test = reed.count('O')
    if test == sise:
        print
        print 'yay!'+player2
        print
        gameon = 0



        
def check():
    global reed
    global mode
    py = 0
    px = 0
    reed = []
    
## check verticly

    for line in game:
        for line in game:
            reed = reed + [game[py][px]]
            py=py+1
            
        checkreed()
        reed = []

        px=px+1
        py = 0
            
    py = 0
    px = 0
    reed = []
    
##  check horosontialy

    for line in game:
        for line in game:
            reed = reed + [game[py][px]]
            px=px+1

        checkreed()
        reed = []

        py=py+1
        px = 0

    py = 0
    px = 0
    reed = []

##  check diagonal 1

    for line in game:
        reed = reed + [game[py][px]]
        py=py+1            
        px=px+1

    checkreed()
    reed = []

    py = 0
    px = 0
    reed = []

##  check diagonal 2
    

    px=sise-1
    for line in game:
        reed = reed + [game[py][px]]
        py=py+1            
        px=px-1

    checkreed()
    reed = []




    




##choose player name
while run > 1:

    
    player1 = raw_input('player 1')
    player2 = raw_input('player 2')

##  choose table sise   
    while x > 0:
        x = 1
        sise = int(raw_input('sise?'))
        if sise < 3:
            print 'to small! _>3'
        elif sise > 20:
            print 'to big!'
        elif sise in range(2,21):
            x = 0
        
## construct gamebord
    for fg in range(0,sise):
        game.append(['?'])
    for x in range(0,sise-1):
        for fh in range(0,sise):
            game[fh] = game[fh]+['?']

##  draw table   
    for line in game:
            print line
            print
## main loop
    while gameon>0:
        if player == 1:
            print player1
        elif player == 2:
            print player2
##      player choose position
            
        while qd in range(1,3):
            placex = input('place x?')-1            
            placey = input('place y?')-1
    ##      check if position is used 

            if game[placey][placex] =='x':
                print
                print 'used!'
            elif game[placey][placex] =='O':
                print
                print 'used!'
            elif game[placey][placex] == '?':
                qd=4
        qd=1
        

        print
##      add  turn to the table  
        if player == 1:
            game[placey][placex] = 'x'

        elif player == 2:
            game[placey][placex] = 'O'

##      test for win      
        check()

##      draw table and switch player
        for line in game:
            print line
            print
        if player == 1:
            player = 2
        elif player == 2:
            player = 1
    game = []

```

any comments?

---

