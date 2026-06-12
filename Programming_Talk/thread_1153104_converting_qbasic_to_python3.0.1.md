---
title: "converting qbasic to python3.0.1"
date: 2009-05-08
forum: Programming Talk
---

### Post by Spidey1980 on 2009-05-08
I'm trying to learn python. The only programming language I've learned so far is qbasic. 
The following program in qbasic has most of the elements I would need to know in python, and seeing it in python would help me a lot. it is a starscape screensaver, with three layers of stars ant different speed and shades (bright white, white, and gray). the stars are round, they grow, and the program reads values from a text file (maxstars, speed, begining radius.
 Here it is in qbasic, using the future library for graphics: 

```

'Starscape by Spidey
'Starscap.txt format is variable to set
'on one line and the value on the next
'line. Variables can go in any order.

REM $INCLUDE: 'future.bi'

OPEN "I", 1, "starscap.txt"
FOR c = 1 TO 3
    INPUT #1, B$
    IF B$ = "maxstars" THEN INPUT #1, maxstars
    IF B$ = "speed" THEN INPUT #1, speed
    IF B$ = "radius" THEN INPUT #1, Radius
NEXT
CLOSE #1

Set1024x768 8
a$ = ""
a = 7
DIM stars(maxstars, a)

DO
 FOR n = 1 TO maxstars
    IF stars(n, 1) < 1 OR stars(n, 2) < 1 OR stars(n, 1) > 1024 OR stars(n, 2) > 768 THEN
        Future.FILLCIRCLE INT(stars(n, 1)), INT(stars(n, 2)), stars(n, 5), 0
        RANDOMIZE TIMER
        v = INT(RND(1) * 200) - 99: w = INT(RND(1) * 200) - 99
        IF v = 0 THEN v = 1: IF w = 0 THEN w = 1
        c = INT(RND(1) * 3) + 1
        SELECT CASE c
            CASE 1
                stars(n, 7) = 15
            CASE 2
                stars(n, 7) = 8
            CASE 3
                stars(n, 7) = 7
        END SELECT
        stars(n, 1) = v + 512: stars(n, 2) = w + 384
        stars(n, 5) = Radius: stars(n, 6) = INT(RND(1) * 10)
        l = SQR((v * v) + (w * w))
        SELECT CASE stars(n, 7)
            CASE 15
                speeda = speed
            CASE 8
                speeda = speed / 4
            CASE 7
                speeda = speed / 2
        END SELECT
        stars(n, 3) = v / l * speeda: stars(n, 4) = w / l * speeda
    END IF
    Future.FILLCIRCLE INT(stars(n, 1)), INT(stars(n, 2)), stars(n, 5), 0
    stars(n, 1) = stars(n, 1) + stars(n, 3)
    stars(n, 2) = stars(n, 2) + stars(n, 4)
    stars(n, 6) = stars(n, 6) + 1
    IF stars(n, 6) / 15 = INT(stars(n, 6) / 15) AND stars(n, 5) < 5 THEN stars(n, 5) = stars(n, 5) + 1
    Future.FILLCIRCLE INT(stars(n, 1)), INT(stars(n, 2)), stars(n, 5), stars(n, 7)
 NEXT
 a$ = INKEY$
LOOP UNTIL a$ <> ""
Palette.FadeOut
ReSetScreen
END

```this is what i have in python so far:
```

f = open ('stasrcap.txt', 'rt')
for c in range (0,5,2)
    b = f.read(c)
    if b == 'maxstars': 
        maxstars = f.read(c+1)
    if b == 'speed':
        speed = f.read(c+1)
    if b == 'radius':
        radius = f.read(c+1)
f.close()


```I plan to use the turtle module for graphics.



the text file reads:

maxstars
150
speed
15
radius
2

Can anyone help me? Am I on the right track?
edit: added code and /code

---

### Post by ajackson on 2009-05-08
Can you wrap your code in [ code ] [ /code ] blocks (without the spaces) as it makes it easier to read.

---

### Post by Spidey1980 on 2009-05-08
Thanks, I did. I got severly lost when trying to understand turtle graphics. Is there a command to initialize it? 
every time i try it says name 'turtle' is not defined

---

### Post by raydeen on 2009-05-08
You'll probably have to import the Turtle module into your program.

```

import Turtle

```

---

### Post by geirha on 2009-05-08
With a little list-comprehension, you can shorten the file parsing a bit
```

lines= [line.strip() for line in file('/tmp/starscap.txt')]
data= dict(zip(lines[::2],[int(x) for x in lines[1::2]]))

print data['maxstars'], data['speed'], data['radius']

```

On the turtle part, it sounds like you haven't imported the turtle module. Try this example I found with google:
[http://www.daniweb.com/code/snippet304.html#](http://www.daniweb.com/code/snippet304.html#)

It's for python 2.4, but it will probably work with python 3.0 as well.

---

### Post by Spidey1980 on 2009-05-08
@geirha: if I read your code correctly, can I then dimension an array using the variable maxstars?
Or do i have to use data['maxstars']? And thanks for the link.

@raydeen: thanks I will expiriment with that, is it {from turtle import *}    OR{import turtle} OR are they the same?


I'm having trouble figuring out python arrays, for example, how would you do this in python? (again, this is QB)

```
 
dim stars(maxstars,2)

```where stars(1,1) is the first star's x pos 
and stars(1,2) is the first star's y pos?

---

### Post by geirha on 2009-05-08
It's only stored in data['maxstars'] in my example, if you want a shorter name, you can always do ```
maxstars= data['maxstars']
```

Also, you don't need to "dimension" arrays in python. Just do something like
```

import random
stars= []
for i in range(data['maxstars']):
    x= random.randint(0,100)
    y= random.randint(0,100)
    stars.append( (x,y) )

```

---

### Post by Spidey1980 on 2009-05-08
alright, and can do math to the x,y like i'm used to? 

```

stars(30,1) = stars(30,1) + 1
stars(30,2) = stars(30,2)  - 1

```

and can those variable be passed directly to turtle graphics, or do I need to save the array data to a simple variable first?

also, i'm trying to have it as stars(starnumber,data set 1) is x and stars(starnumber, data set 2) is y; does that make any sense?

---

### Post by geirha on 2009-05-08
If you make it a list of lists (instead of list of tuples as I used in my example), you should be able to do something like that.

```

import random
stars= []
for i in range(data['maxstars']):
    x= random.randint(0,100)
    y= random.randint(0,100)
    stars.append( **[**x,y**]** )

stars[0][0] += 1   # increment first star's x coordinate
stars[0][1] -= 1   # decrement first star's y coordinate

```

---

### Post by Spidey1980 on 2009-05-08
thank you Geirha.

my other question is this; however this may not be the place to ask.

Once compiled to a .exe , I know I can change the extension to . scr for a screen saver but somehow I need to add some extra data to make it an usable window screen saver. does anyone know how this is accomplished?

---

### Post by Spidey1980 on 2009-05-09
this is the last time for a week that i can get on
gierha I can tell that there are a few errors in your example according to what i need to do however you did give me the basis for what i need to complete the conversion so I thank you......stars[0] [0] instead of stars (0,0).

---

### Post by Spidey1980 on 2009-05-09
but tell me does stars[0] [0] [0] in python mean the same as stars(0,0,0) does in basic?

ex: stars[star number; maxstars bits] [star layer(back, mid, or foreground; color or shade of star); one bit] [x or y pos. of star; two bits]
or: array of stars[star number to maxstars] [layer 1, 2, or 3] [position x or y]
stars[0] [0] [1] for max arguments
stars[Maxstars] [Layer] [0] for x
stars[Maxstars] [Layer] [1] for y

and can i exec commands from a .txt or .cfg for example, if I construct my config (text) file as
```

maxstars == 100
speed == 15
radius == 2

```is there a command in python to read and execute commands from that file?  To set the variables? that would be quicker than parsing it in in my own code.

also, some one else gave me the vertex math for 0,0 in top left, but stars starting in center of screen, I don't get the math, but would that have to be changed for 0,0 in center of screen? the Turtle graphics can do 0,0 where ever you want but I think it can be faster with 0,0 at center not top left.

sorry I haven't had time to try it my self but PLEASE do not do the full conversion for me I need to learn I have several money magnet program ideas.  I need to do this my self but your help in small ways is very appreciated.

---

### Post by geirha on 2009-05-10
Yes, you can have as many dimensions as you like (well, as many as there are memory for), so if you make a list of list of lists, you can access the elements with stars[a][b][c]. You might want to look into classes btw, and just use a list of star objects instead.

There is the eval function that will take a string as argument, and execute it as python code, but it's generally considered bad practise to use eval. Have a look at the ConfigParser module. I think it would be better to learn how to use that (for later python projects you may undertake) [http://docs.python.org/library/configparser.html](http://docs.python.org/library/configparser.html)

As for the vertex math. I don't know. Haven't seen the math you are talking about, but if your qbasic program uses 0,0 as center, and you can tell turtle to use 0,0 as center, then just try translating the math directly from qbasic to python.

---

### Post by Spidey1980 on 2009-08-27
Wow sorry haven't had time for programing with new job all............
thank you for all your help and i may return if I have other question, how ever the math is in this section of code i originally posted, i am adding Remark statement to document this time:

```

'v is x is 1st coord, w is y is 2nd coord.,half width/height to get center
' v & w are set randomly when a star is born in the center
stars(n, 1) = v + 512: stars(n, 2) = w + 384

' size, I forget what data slot 6 is for, n is star I.D. number
stars(n, 5) = Radius: stars(n, 6) = INT(RND(1) * 10):

'somehow this finds angle in vertices (more than 360 degrees in a circle)
'stars start outside the bullseye zone,angle is center 0,0 to stars x,y 
l = SQR((v * v) + (w * w)) 

'this sets speed of star, based on color of star, 3 layers. 
'background, dark, slow. midground, dim, medium. foreground, bright, fast.
'also closer foreground stars start larger than stars further away in the background
SELECT CASE stars(n, 7)
            CASE 15
                speeda = speed
            CASE 8
                speeda = speed / 4
            CASE 7
                speeda = speed / 2
END SELECT
        
'this takes that angle calculation * speed and sets new star position 
stars(n, 3) = v / l * speeda: stars(n, 4) = w / l * speeda

```then you erase the old star,  move new position data to current position data, and draw new star.  Sound simple, right?

---

