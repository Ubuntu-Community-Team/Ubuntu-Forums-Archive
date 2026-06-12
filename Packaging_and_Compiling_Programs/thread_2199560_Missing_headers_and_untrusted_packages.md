---
title: "Missing headers and untrusted packages"
date: 2014-01-14
forum: Packaging and Compiling Programs
---

### Post by linuxonbute on 2014-01-14
Hi all,
I am running 12.04 which is completely up to date.
Python 2.7.3 (default, Sep 26 2013, 20:03:06) 

I want to develop a simple oscilloscope using a board which I subscribed to via kickstarter.
It is a micropython board and has a number of fast ADC's on it.
What I want to do is write a program on my PC which can read the data the board will store in a file and then display it on my computer screen.
Now I have done a similar thing with my arduino and using the processing language on my computer but it will only work up to a little over audio frequencies due to the limitations of the arduino's adc and the serial interface ( the way data was sent to my PC )
Now my problem.
I thought I would use python on my PC as well as on the board but I am really not succeeding with it.
Here is the code I wrote which just uses random to generate the "input"
```

#!/usr/bin/python
#from array import *
from graphics import *
import random
import time


xpos=1200
ypos=400


def main():
    win = GraphWin("My Circle", xpos, ypos, autoflush=False)
    win.config(bg="light blue")


    for y in range(1,25):
        update()
        cir = Circle(Point(xpos/2,20), 10)
        cir.setFill("white")
        cir.draw(win)
        message = Text(Point(win.getWidth()/2, 20), y)
        message.draw(win)
        j = random.randint(1,ypos)
        for x in range(1,xpos):
            updown = random.randint(0,1)
            if updown:
                j=j+1
            else:
                j=j-1
            if j <1:
                j=ypos/2
            if j>ypos-1:
                j=ypos/2
            win.plot(x,j,"red")
#            undraw(x,store[x])




main()
time.sleep(3)


```

This works as is but if you run it you will see that it draws all the lines though I would want to just display each one in turn.
I have been using the graphics.py module   (  [http://mcsp.wartburg.edu/zelle/python/graphics/graphics/index.html](http://mcsp.wartburg.edu/zelle/python/graphics/graphics/index.html) )

It indicates there that undraw works but it fails and I cannot seem to remove the old line before or as I draw a new one. 
It seems this is not an ideal module to use so I have tried doing it differently without success for the following reasons:
1/ Tried opengl SDL tkinter and so on but always something is missing, usually a header and hours of searching doesn't resolve the problem.

2/ Installation fails due to untrusted packages.

3/ using apt-get install of these which allows me to install them at my own risk still ends up with something missing.

Example problems:
> 
gcc tut1.c  -lGL $(sdl-config --cflags --libs)
tut1.c:6:19: fatal error: GL3/gl3: No such file or directory
compilation terminated.

And just about everything else I have tried results in something missing

Here is another problem I get when I try to install stuff
> 
I tried to install Eric Python IDE and get the error about untrusted packages. These:
bicyclerepair eric eric-api-files libqscintilla2-8 libqtassistantclient4 libreadline5 python-pygments python-qscintilla2 python-qt4 python-sip ruby vim-addon-manager

I seem to get this problem with untrusted packages **even synaptic** which I thought would at least show me packages which might indicate that they contained  the missing modules etc.
Now this untrusted packages problem seems to have increased e[FONT=Bitstream Charter]xponentially [/FONT]since I moved to Ubuntu 12.04.
I'm sorry this is such a long post.
Is there any way I can resolve this please?

---

### Post by linuxonbute on 2014-01-19
I have managed to sort out the untrusted packages problem but not the embedding problem.

---

