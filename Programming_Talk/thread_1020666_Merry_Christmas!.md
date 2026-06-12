---
title: "Merry Christmas!"
date: 2008-12-24
forum: Programming Talk
---

### Post by nvteighen on 2008-12-24
As this subforum is a place where there's a lot of regulars that we know eachother, to the extent that we could name each one's favorite programming language, reproduce each one's arguments and leitmotifs... I wish all the programmers, Pythonistas and Perl Monks, Common Lispers and Schemers, C-guys/gals, C#, C++, Java and Ruby programers, Web-developers and ASM geeks a **Merry Christmas**...

...in a Forth program! :D

```

( xmas.fs )
: xmas ( n -- )
    ." Merry Christmas and Happy New Year " 1 + .
    ." !!"
;

2008 xmas
cr

```

Install **gforth** and run using:
```

gforth xmas.fs -e bye

```

:)

EDIT: If someone could, please, tell me how to accept numerical input from user, I'd improve this...

---

### Post by pmasiar on 2008-12-24
> **nvteighen said:**
> how to accept numerical input from user, I'd improve this...

define IMMEDIATE word. Check how ." is defined. :-)

---

### Post by CptPicard on 2008-12-24
It is an interesting thought that yes, we would probably be able to pull off reasonable impressions (parodies?) of each other's posts. Yet, it is ever enjoyable to hear them over and over again ;)

As a y-combinator side-effect of this post, I would like to wish everyone a Merry Christmas as well.

```

((lambda (x) (x x)) 
 (lambda (x)
   (display "Merry Christmas!")
   (newline)
   (x x)))

```

---

### Post by s3gfault on 2008-12-24
Merry Xmas!

```
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.
++++++++++++++++++++++++.
+++++++++++++.
.
+++++++.
-----------------------------------------------------------------------------------------.
+++++++++++++++++++++++++++++++++++.
+++++++++++++++++++++++++++++++++++++.
++++++++++.
---------.
++++++++++.
+.
-------.
------------.
++++++++++++++++++.
-----------------------------------------------------------------------------------.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.
+++++++++++++.
----------.
--------------------------------------------------------------------.
++++++++++++++++++++++++++++++++++++++++.
+++++++++++++++++++++++++.
+++++++++++++++.
.
+++++++++.
-----------------------------------------------------------------------------------------.
++++++++++++++++++++++++++++++++++++++++++++++.
+++++++++++++++++++++++.
++++++++++++++++++.
---------------------------------------------------------------------------------------.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++.
++++++++++++.
----.
+++++++++++++++++.
----------------------------------------------------------------------------------.
++++++++++++++++++.
--.
.
+++++++++.
-------------------------.
+.
.
-----------------------.
```
How to run:
1) save to xmas.bf
2) apt-get install bf
3) bf xmas.bf

---

### Post by snova on 2008-12-24
[PHP]eval('r(r)',{'r':lambda s:print("Merry Christmas!")==s(s)})[/PHP]

Merry Christmas to all! :)

---

### Post by Wybiral on 2008-12-24
Merry Christmas in PyGame + PyOpenGL:
```

import pygame
from OpenGL.GL import *
from OpenGL.GLU import *
from math import radians, cos

class Text:
    def __init__(self, text, size, fg, bg):
        font = pygame.font.Font(pygame.font.get_default_font(), size)
        message = font.render(text, 1, fg, bg)
        self.width, self.height = message.get_rect().size
        self.scale = 0.5 / self.height

        data = pygame.image.tostring(message, 'RGBA', 1)

        # Dirty hack to get alpha transparency on text renders
        out = [] 
        for i in xrange(0, len(data), 4):
            r, g, b = data[i], data[i+1], data[i+2]
            out.extend([r, g, b, max(r, max(g, b))])
        data = ''.join(out)
        
        texture = glGenTextures(1)
        glBindTexture(GL_TEXTURE_2D, texture)
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR)
        glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR)
        glTexImage2D(GL_TEXTURE_2D, 0, GL_RGBA, self.width, self.height,
                     0, GL_RGBA, GL_UNSIGNED_BYTE, data)
        self.build(texture)
        
    def build(self, texture):
        self.gl_list = glGenLists(1)
        glNewList(self.gl_list, GL_COMPILE)
        glPushMatrix()
        glScalef(self.scale, self.scale, 1.0)
        glBindTexture(GL_TEXTURE_2D, texture)
        glBegin(GL_QUADS)
        glTexCoord2f(0.0, 0.0)
        glVertex2f(-self.width, -self.height)
        glTexCoord2f(1.0, 0.0)
        glVertex2f( self.width, -self.height)
        glTexCoord2f(1.0, 1.0)
        glVertex2f( self.width,  self.height)
        glTexCoord2f(0.0, 1.0)
        glVertex2f(-self.width,  self.height)
        glEnd()
        glPopMatrix()
        glEndList()

    def render(self):
        glCallList(self.gl_list)
        

# Window dimensions
width = 320
height = 200

# Setup PyGame
pygame.init()
pygame.display.set_mode((width, height), pygame.DOUBLEBUF | pygame.OPENGL)
pygame.display.set_caption('Merry Christmas!')

# Setup OpenGL
glMatrixMode(GL_PROJECTION)
gluPerspective(60, float(width) / height, 0.01, 6000)
glMatrixMode(GL_MODELVIEW)
glEnable(GL_DEPTH_TEST)
glEnable(GL_TEXTURE_2D)

# Setup alpha clipping
glEnable(GL_ALPHA_TEST)
glAlphaFunc(GL_GREATER, 0.5)

# Setup fog
glClearColor(0, 0, 0, 0)
glFogi(GL_FOG_MODE, GL_EXP)
glFogfv(GL_FOG_COLOR, (0, 0, 0))
glFogf(GL_FOG_DENSITY, 0.25)
glHint(GL_FOG_HINT, GL_DONT_CARE)
glFogf(GL_FOG_START, 1.0)
glFogf(GL_FOG_END, 5.0)
glEnable(GL_FOG)    

# Build text objects
merry = Text('Merry', 32, (255, 0, 0, 255), (0, 0, 0))
christmas = Text('Christmas', 32, (0, 255, 0), (0, 0, 0))
programming_talk = Text('Programming Talk!', 32, (255, 255, 255), (0, 0, 0))

angle = 0.0
clock = pygame.time.Clock()
running = True
while running:
    clock.tick(50)
    angle += 2.0
    
    # Constrain angle to 0-360 range
    if angle > 360.0:
        angle -= 360.0

    glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT)
    glPushMatrix()
    glTranslatef(0.0, 0.0, -7.0)
    glRotatef(cos(radians(angle)) * 50, 0.0, 1.0, 0.0)
    glTranslatef(0.0, 0.5, 3.0)
    merry.render()
    glTranslatef(0.0, -0.5, -1.5)
    christmas.render()
    glTranslatef(0.0, -0.5, -1.5)
    programming_talk.render()
    glPopMatrix()
    pygame.display.flip()

    # Check for exit/escape events
    for i in pygame.event.get():
        escaped = (i.type == pygame.KEYDOWN and i.key == pygame.K_ESCAPE)
        if i.type == pygame.QUIT or escaped:
            running = False

```

---

### Post by OutOfReach on 2008-12-24
C:
[PHP]
#include <stdio.h>

int main(void)
{
    printf("Merry Christmas!\n");

    return 0;
}
[/PHP]

Merry Christmas to all, and Happy New Year too. :)

---

### Post by pp. on 2008-12-24
echo "Merry Christmas"

([http://ubuntuforums.org/showthread.php?t=497579](http://ubuntuforums.org/showthread.php?t=497579))

---

### Post by Sprut1 on 2008-12-24
```

class Xmas:
    def __init__(self):
        print "Merry Christmas"


```

---

### Post by gettinoriginal on 2008-12-24
As an end user with no knowledge of programming (except my vcr LOL)  I would like to thank you all for your contributions and hard work.

Merry Christmas, Happy Hannuka, and Happy Holidays to each and all

---

### Post by kostkon on 2008-12-24
Java:
```
public class ChristmasWisher {
         
   private String christmasWishStr;

   public ChristmasWisher() {
      this.christmasWishStr = "Merry Christmas!";
   }

   public String getChristmasWish() {
      return this.christmasWishStr;
   }

   public static void main(String[] args) {

      ChristmasWisher cw = new ChristmasWisher();
      System.out.println(cw.getChristmasWish());
   }
}
```

compile
```
javac ChristmasWisher.java
```
run
```
java ChristmasWisher
```

---

### Post by Sorivenul on 2008-12-25
Holiday wishes from myself and Haskell:
[PHP]main = do putStrLn "What name should go on your greeting card? "
          name <- getLine
          putStr ("Happy Holidays, " ++ name ++ "!\n")[/PHP]

---

### Post by Grant A. on 2008-12-25
This needs a text-based python game!

Here's a hint: It's possibly the most pointless game in existence.

Source:

```

# This code is licensed under the BSD License

welcome = raw_input("Welcome to the holiday quizzer. If you guess the holiday the creator of the program celebrates then you win! Press 'I' for the instructions, 'Q' to quit, or 'S' to start: ")

if welcome == "I" or welcome == "i":
    intro = raw_input("\nTo play choose the capital letter of the correct answer and then press enter. Press 'Q' to quit, or 'S' to continue: ")

    if intro == "S" or intro == "s":
        welcome = "S"

    elif intro == "Q" or intro == "q":
        raw_input("\nPress enter to quit.")
        welcome = "Q"

    else:
        raw_input("\nError! Press enter to quit.")
        welcome = "Q"

elif welcome == "Q" or welcome == "q":
    raw_input("\nPress enter to quit.")
    
while (welcome == "S" or welcome == "s"):
    print "\nIs it:"
    print "\nA) Kwanzaa"
    print "B) Hanukkah"
    print "C) Christmas"
    print "D) Winter Solstice"

    answer = raw_input("\nI choose: (Capital letters only!) ")
    
    while (answer != "C"):
        answer = raw_input("\nWrong! Try again: ")

    if answer == "C":
        raw_input("\nCorrect!")
        raw_input("\nPress enter to quit.")
        welcome = "Q"

    else:
        answer = "i"

```

Download:

---

### Post by dannytatom on 2008-12-25
Merry Christmas all :)

& in Ruby:
```

puts "I'm Father Christmas, and your name is?"
name = gets.strip
puts "Well Merry Christmas, #{name}!"

```

---

### Post by nvteighen on 2008-12-25
> **pmasiar said:**
> define IMMEDIATE word. Check how ." is defined. :-)

Hmm... My problem is how to transform a string into a number after storing it through 'accept'. '>number', 's>number?' and friends aren't working for me...

---

### Post by jimi_hendrix on 2008-12-25
tcl

```
puts "Merry Christmas"
```

C#

```

using System;

class Xmas
{
    static void Main()
    {
         Console.WriteLine("Merry Christmas");
    }
}

```


C++
```

#include <iostream>

int main()
{
   std::cout << "Merry Christmas" << std::endl;
   return 0;
}

```

---

### Post by WitchCraft on 2008-12-25
Merry Christmas via /dev/null, wget, grep and sed!

```

wget -O - http://www.phys.msu.ru/eng/news/archive/20031231001/ 2> /dev/null | grep "New Year" | sed 's/<[^>]*>//g;s/^\s*//g;s/Vladimir Trukhin/WitchCraft,/;s/Physics/SedHacking/'

```

Enjoy your 99 bottles of beer!
```

wget -q -O - http://99-bottles-of-beer.net/lyrics.html 2> /dev/null | grep "be" | tr -d '\012' | sed ';s/<[^>]*>//g;s/^\s*//g;s/er\./er\.\n/g;s/ll\./ll\.\n\n/g;' | sed 's/^\s*//g'

```

and another 99 bottles:
```

 wget -q -O - http://99-bottles-of-beer.net/lyrics.html 2> /dev/null | sed ':a;N;$!ba;s/\n//g;s/.*<\/li>//;s/Start.*//;s/<\/p><p>/\n/g;s/<br>/\n/g;s/<br\/>/\n\n/g;s/<[^>]*>//g;s/^\s*//g'


```

---

### Post by jimi_hendrix on 2008-12-25
here it is in F#

```

#light
let message = "Merry Christmas! \n";;
open System;;
printfn "%s" message;;
Console.ReadKey(true);;

```

---

