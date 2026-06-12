---
title: "Embedding a matplotlib graph in a Tkinter window"
date: 2014-01-20
forum: Programming Talk
---

### Post by linuxonbute on 2014-01-20
I have python 2.7.3 installed on my 12.04 64 bit system. I have written the following:
```

#!/usr/bin/env python 
import  numpy as np
from  matplotlib import  pyplot as plt
import time
import sys


if len(sys.argv) < 2:
    sys.stderr.write("\n\n\nUsage: " + sys.argv[0] + " needs to know how many points to display\n\n           .. Like this: " + sys.argv[0]  + " 50\n\n\n")
    sys.exit(1)
howmany = int(sys.argv[1])
top = 100
plt.ion () # set plot to animated
xdata = []
c = 0
for a in range(0,top):
    xdata.append(a)
    c+=1
ydata =  [ 0 ] *  top * 10
ax1 = plt.axes ()  
c = 0
myfile = open("rdata.txt", "r")
for myline in myfile:
    q = myline
    ydata[c] = q 
    c+=1
c = 0
# Make plot
line, =  plt.plot (ydata[0:howmany])


myfile = open("rdata.txt", "r")


for p in range(0, top * 10):
#for myline in myfile:
#    q = int(myline)
#    ydata.append (q)
        del  ydata [ 0 ]
        line.set_xdata (np.arange ( len (ydata)))
        line.set_ydata (ydata)   # update the data
#          time.sleep(0.01)
        plt.draw () # update the plot    


#    c +=1




file.close(myfile)




```
It reads data from a file I generated using random data.

Ultimately I want to use it with a micropython board ( a kickstarter project which has python on a microcontroller ) to make a simple form of oscilloscope.
The code above displays a dynamic graph which looks just like an oscilloscope display but obviously I want to do more.
As you will see if you run it, the display is constantly updated until it has read all the data then ends.
What I want to do is get it embedded so the wrapper includes entry, button and other widgets so I can customise the graph from a GUI rather than pass command line parameters. Everything I have found after hours of searching works fine IF you just want a static display.
For example I tried to modify the following to embed it:
```

#!/usr/bin/env python
import matplotlib, sys
matplotlib.use('TkAgg')
from numpy import arange, sin, pi
from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg, NavigationToolbar2TkAgg
from matplotlib.figure import Figure
from Tkinter import *
from functools import partial as pto


master = Tk()
master.title("Hello World!")
#-------------------------------------------------------------------------------
f = Figure(figsize=(5,4), dpi=100)
a = f.add_subplot(111)
t = arange(0.0,3.0,0.01)
s = sin(2*pi*t)
a.plot(t, s)


dataPlot = FigureCanvasTkAgg(f, master=master)
dataPlot.show()
dataPlot.get_tk_widget().pack(side=TOP, fill=BOTH, expand=1)
#-------------------------------------------------------------------------------


master.mainloop()


```

But I cannot find out how I can get it to set s to a value in the ydata[] array.
I have tried, for example:
```



f = Figure(figsize=(5,4), dpi=100)
a = f.add_subplot(111)
t = arange(0.0,3.0,0.01)
for x in range(0,50):
    s = ydata[x]
    a.plot(t, s)



```
and many other ideas but I get all sorts of different errors and if, by some chance some of it works, the plot window detaches from the main window and just displays some static plot.
Any ideas please?
I won't be able to answer this soon if you have any questions until tonight though.

---

### Post by 23dornot23d on 2014-01-26
Maybe you could pick something out of this example

[http://www.physics.utoronto.ca/~phy326/python/Live_Plot_Simple.py](http://www.physics.utoronto.ca/~phy326/python/Live_Plot_Simple.py)

I did a small video to show it working ...... but its the best I could do with my limited knowledge of python and tk

maybe someone else can help - but saw there was no response to this for 5 days now .....

[http://youtu.be/tYKM-BK-nGQ](http://youtu.be/tYKM-BK-nGQ)

Also stackoverflow.com is a good place for this type of question

I had to uninstall and rebuild matplotlib to get things working .... so maybe that might help
also loaded in tk-dev ...... before doing the rebuild ..... 
( hope something here gives you a chance to move it on a little further )

[http://stackoverflow.com/questions/13110403/matplotlib-backend-missing-modules-with-underscore](http://stackoverflow.com/questions/13110403/matplotlib-backend-missing-modules-with-underscore)

---

### Post by linuxonbute on 2014-01-26
Thanks for the reply I had just about given up and was thinking I would stick to the command line. 
I tried copying and pasting the code you suggested but on running it unmodified I got some errors.

I too am a beginner with tk/tkinter although I do know a fraction more python but I needed to change every instance of 

```

ticks.append(clock())

```
to
```

ticks.append(time.clock())  

```

I seem to have the same problem with this code as the others I have tried. It's still a matplotlib window and not embedded in, for example, a cell in a grid. Also, as it states it slows down as the number of points increases. If you try the code I have posted you will find this does not happen because only a fixed number of points are displayed although of course these are different as at each iteration the first one has been removed and a new one tacked on at the end.

---

### Post by 23dornot23d on 2014-01-26
I have loaded quite a lot of things in for Python and run version 2.7.3 not sure if it makes a big difference which is run

but here is a small listing of the main things that I have loaded up ....... as I did not need to change anything in that

script to get it to work ............ so maybe either some packages are missing or something else to do with the version

of Python may be causing problems ........

This link is to where I am messing around with Python for a blackboard program I am trying to make - but its a bit of a 

hack together .......... but the last page has most of my setup files on it ......... and some more information as to how I

went about setting things up using  ....... [https://sites.google.com/site/pythonlearnthehardway/setup-page-python](https://sites.google.com/site/pythonlearnthehardway/setup-page-python)

pip install filename.py --upgrade

might be that numpy or matplotlib need updating ..... there is a script to run that finds the updated packages too .......

Will add a link to it .........

Not sure how we can tell which files might be missing ....... but I will try to find a way to get a better listing from my

setup - but its constantly changing .........

---

### Post by linuxonbute on 2014-01-27
[COLOR=#000000]I hunted around for hours after your first post and finally found some code which would do mostly what I want.[/COLOR]
[COLOR=#000000]I still cannot embed the matplotlib window in a grid and had already given up using pack()
[/COLOR]I get a window in which I can enter how many points to display in the matplotlib window. When I click on the 'Draw Graph' window a matplot lib window appears somewhere else on the screen. When the whoe number of points has been displayed this new window closes. It's okay but it isn't entirely what I want and doesn't look right as an application.
[COLOR=#000000]I will play around with this some more but here is what I have so far:

[/COLOR]```
#!/usr/bin/env python
import Tkinter
from tkSimpleDialog import *
import math
import string
from  matplotlib import  pyplot as plt
import  numpy as np

def callback():
    sys.exit() 

def plotit():
#    if (Entry.get(x) < "1"):
#       text.text = "value must be more then zero"
#        plt.close()

    howmany = int(Entry.get(x))
    top = 100
    plt.ion () # set plot to animated
    xdata = []
    c = 0
    for a in range(0,top):
        xdata.append(a)
        c+=1
    ydata =  [ 0 ] *  top * 10
    ax1 = plt.axes ()  
    c = 0
    myfile = open("rdata.txt", "r")
    for myline in myfile:
        q = myline
        ydata[c] = q 
        c+=1
    c = 0
# Make plot
    line, =  plt.plot (ydata[0:howmany])

    myfile = open("rdata.txt", "r")
    for p in range(0, top * 10):
        del  ydata [ 0 ]
        line.set_xdata (np.arange ( len (ydata)))
        line.set_ydata (ydata)   # update the data
        plt.draw () # update the plot    
    file.close(myfile)
    plt.close()


root = Tkinter.Tk()
 
x = Entry(root)
x.grid(row=1, column=0, columnspan=2)
text = Label(root, text="Enter the number of points to display below")
text.grid(row=0, column=0)
button1 = Button(text="Exit", command=callback).grid(row=2, column=2, sticky=SE)
Button(root, text='Plot', command=plotit).grid(row=2, column=3, columnspan=1)
 
root.mainloop()
```[COLOR=#000000]
[/COLOR][COLOR=#000000]and I used the following to generate the random data:
[/COLOR]```

[COLOR=#000000]

#!/usr/bin/env python
from random import randint
myfile = open("rdata.txt", "w")
for p in range(0, 1000):
    q = str(randint(4,90)) + "\n"
    myfile.write(q)

myfile.close()[/COLOR]

```[COLOR=#000000]
If you choose a small number of points, around 50 to 150 to display then it looks quite good.[/COLOR]
[COLOR=#000000]I still need to figure out a few bits like error checking on the input into the Entry box.
I also want to do extra bits relating to selecting a range out of the total number of points out of the total available.[/COLOR]

---

### Post by 23dornot23d on 2014-01-27
I added a few debugging print statements to see what was happening ..... here is what I have so far

[IMG]http://i.minus.com/i6gZmrEr71xPW.jpg[/IMG]

The data file that was created from your script is here to 

Download this for the data I used 
[https://sites.google.com/site/pythonlearnthehardway/setup-page-python/rdata.txt?attredirects=0&d=1](https://sites.google.com/site/pythonlearnthehardway/setup-page-python/rdata.txt?attredirects=0&d=1)

The file is just called u1.py
Download file here [https://sites.google.com/site/pythonlearnthehardway/setup-page-python/u1.py?attredirects=0&d=1](https://sites.google.com/site/pythonlearnthehardway/setup-page-python/u1.py?attredirects=0&d=1)

---

### Post by 23dornot23d on 2014-01-30
I think that this is the best example and description I have found so far that meets the criteria required here ...... 

[http://www.lebsanft.org/?p=48](http://www.lebsanft.org/?p=48)

but all my own efforts so far to reproduce a fully dynamic running example have failed 

( I have gone from Ubuntu to Debian ) the results are much the same - often no graph or one that shows for a instant and is gone ..........

I used a older system = ubuntu 12.04 where it appears to start to work and that is the example I showed above in the screenshot

[IMG]http://i.minus.com/iMnZ8CiKF6UNt.jpg[/IMG]

Just adding to this - one thing that gives me confidence in this being used for real time recording and display
in this blog - if you watch the video ..... real time sound recording with a graph connected to the input which is
a microphone ( or in his case a speaker used as a microphone ) .....
[http://www.swharden.com/blog/2013-05-09-realtime-fft-audio-visualization-with-python/](http://www.swharden.com/blog/2013-05-09-realtime-fft-audio-visualization-with-python/)

Hope something here helps .... 

____________________________________________________________________________

Still not given in on this - as it interests me to see how a live feed could be shown in a graph ...... 
but using the methods shown so far - it will probably be a very slow one as explained in the link above  .......

---

### Post by linuxonbute on 2014-01-30
Well I have been looking more closely at matplotlib widgets and came across some example code. I decided to port the part of my code into one of these and now I only need the matplotlib window. So far I have added 2 of my own buttons and a slider which do what I want more or less so I here is that code:
```


#!/usr/bin/env python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import Button, Slider
import sys


freqs = np.arange(2, 20, 3)


fig, ax = plt.subplots()
plt.subplots_adjust(bottom=0.20, top= 0.90)
plt.ion
axcolor = 'lightgoldenrodyellow'


def endit(mock):  # mock isn't used it's only there cos an error was reported that the function wasn't expecting a parameter and so failed.
    sys.exit() 

def update(val):
    howmany = int(axvals.val)


def plotit(dummy):  # dummy isn't used it's only there cos an error was reported that the function wasn't expecting a parameter and so failed.
    howmany = int(axvals.val)  #int(Entry.get(x))
    top = 100
    plt.ion () # set plot to animated
    xdata = []
    c = 0
    for a in range(0,top):
        xdata.append(a)
        c+=1
    ydata =  [ 0 ] *  top * 10
    ax1 = plt.axes ()  
    c = 0
    myfile = open("rdata.txt", "r")
    for myline in myfile:
        q = myline
        ydata[c] = q 
        c+=1
    c = 0
# Make plot
    line, =  plt.plot (ydata[0:howmany])
    myfile = open("rdata.txt", "r")


    for p in range(0, top * 10):
        del  ydata [ 0 ]
        line.set_xdata (np.arange ( len (ydata)))
        line.set_ydata (ydata)   # update the data
        plt.draw () # update the plot    
    file.close(myfile)
#    plt.close()


#callback = plotit()
axvals = plt.axes([0.15, 0.075, 0.45, 0.03], axisbg=axcolor)
#axamp  = plt.axes([0.25, 0.15, 0.65, 0.03], axisbg=axcolor)


axout = plt.axes([0.81, 0.05, 0.1, 0.075])
aout = Button(axout, 'Exit')
aout.on_clicked(endit)
axplot = plt.axes([0.7, 0.05, 0.1, 0.075])
aplot = Button(axplot, 'Plot')
aplot.on_clicked(plotit)
axvals = Slider(axvals, 'Points\nto plot', 10, 800)


plt.show()



```
It uses the same data file as before and I want to do more with it. I need to figure out how to position the window displayed on the screen and how to set it's size to what I want. Then i intend to add perhaps 2 Entry Boxes so i can thel it which data point in the file to start at and which one to end at.
Although I may decide to do more with it.
To a real programmer this code is probably very crude so if your looking at it by all means suggest inprovements.
I hope this helps you.

---

### Post by 23dornot23d on 2014-01-31
Sorted - but all to do with a pause ........ after the draw ......

Download the file here to check it out .......... 

[https://sites.google.com/site/pythonlearnthehardway/setup-page-python/u9b.py?attredirects=0&d=1](https://sites.google.com/site/pythonlearnthehardway/setup-page-python/u9b.py?attredirects=0&d=1)
same data file
[https://sites.google.com/site/pythonlearnthehardway/setup-page-python/rdata.txt?attredirects=0&d=1](https://sites.google.com/site/pythonlearnthehardway/setup-page-python/rdata.txt?attredirects=0&d=1)

Will post a video of it running shortly ....... just in case this does not work the same on all systems.

No idea why the quality is not good in the video ..... but at least it shows its working ok now 

[http://youtu.be/f7UmMLHWPYs](http://youtu.be/f7UmMLHWPYs)

---

### Post by linuxonbute on 2014-01-31
I got rid of the print statements and saw this:

> 
  /usr/lib/pymodules/python2.7/matplotlib/backend_bases.py:2280: MatplotlibDeprecationWarning: Using default event loop until function specific to this GUI is implemented  warnings.warn(str, mplDeprecation)


I find your changes interesting but I have developed my own code further in line with what I eventually want it to do.
For example I found out how to get the window full screen:
changed 
```

fig, ax = plt.subplots()

```

to 

```

fig, ax = plt.subplots(figsize=(17, 10))

```

17 is the width and 10 the height of the window.

---

### Post by 23dornot23d on 2014-01-31
Looking good now .... also checked it in debian too ........... and its working fine ............

Here is the code with that latest addition you made and some labels in the loop as they disappear otherwise ...........
not sure if it is any use to you - but its here to look at anyway.
u9c.py
[https://sites.google.com/site/pythonlearnthehardway/setup-page-python/u9c.py?attredirects=0&d=1](https://sites.google.com/site/pythonlearnthehardway/setup-page-python/u9c.py?attredirects=0&d=1)

rdata.txt
[https://sites.google.com/site/pythonlearnthehardway/setup-page-python/rdata.txt?attredirects=0&d=1](https://sites.google.com/site/pythonlearnthehardway/setup-page-python/rdata.txt?attredirects=0&d=1)

Its interesting following up on the error messages .......... as I say I am only learning too so your additional
information is giving me ideas for other things and also helping along with my other project.

So we can carry on if you want adding and discussing this ............ its interesting and also making me find new
things that python and all the routines / modules can do to make things better for animating things.

I am still not sure about positioning the windows ......... but as you have found out that is a good way to use the full window.

Will go back through this thread now and see what other things are required ........

---

### Post by linuxonbute on 2014-02-01
I think it could be useful to post anything we find out about configuration of different parts.
Being a simple guy I usually find it easier to understand this sort of stuff if there is an example but I am finding that this doesn't seem to be the case with matplotlib and pyplot.
Here are a few other things I have found:

Change slider background colour
```

#axcolor = 'lightblue'
axcolor = 'lightgrey'    #  comment out all but the one you want. Not tried all possible colours - no idea what they are anyway
#axcolor = 'lightgoldenrodyellow'
#axcolor = 'white'

```

Change slider foreground colour  ( facecolor )
```

axvals = plt.axes([0.25, 0.05, 0.42, 0.025], axisbg=axcolor)
axvals = Slider(axvals, 'Points to\n display', 10, 100, valfmt='%1.0f', facecolor='lightgreen')
axvals1 = plt.axes([0.25, 0.10, 0.42, 0.025], axisbg=axcolor)
axvals1 = Slider(axvals1, 'Pause', 0, 1.0, valfmt='%1.2f', facecolor='lightgreen')

```

---

### Post by 23dornot23d on 2014-02-01
This was where I started with Tkinter ..... got the colour selection dialog from here for choosing colours to use
then had to learn how to strip out the parts that I needed from the output for individual colours to re-use them.
( if I am writing any new snippets of code that I find useful - I will post as you have done - maybe we will end up with a small library here of useful
snippets as we progress )
[http://www.python-course.eu/tkinter_dialogs.php](http://www.python-course.eu/tkinter_dialogs.php)

I use this examples page for matplotlib quite a lot to refer to too ... [http://matplotlib.org/1.3.1/examples/index.html](http://matplotlib.org/1.3.1/examples/index.html)

Not all examples seem to work without having to do more hunting around for other python programs - but often the
error messages given are pretty good for seeing where to go to next. ( will also post other example pages as I come across them)

Cheers for the code above too .... the slider and the input is a good way to quickly add data - or set defaults up - ready for modifications.

Some of the searches too come up with diagrams that look interesting - then I go dig out the code to examine . 

( searching the IMAGES ..... seems a quick way to see if anything may be useful ....... may seem obvious ..... but when I first started I just
kept going from one web page to the next trawling through loads of text ........ usually if the blogger has been good enough to supply a decent 
picture of what it was they were doing - its a good indication they set the page out easy to follow too ....... )

[https://www.google.co.uk/search?q=python+trig_waves&client=ubuntu&](https://www.google.co.uk/search?q=python+trig_waves&client=ubuntu&)

---

### Post by linuxonbute on 2014-02-02
I have found this:
[http://www.verious.com/tutorial/16-common-python-runtime-errors-beginners-find/](http://www.verious.com/tutorial/16-common-python-runtime-errors-beginners-find/)
gives some good error pointers.

Also good for labelling
```

ax.set_ylabel('Voltage')
ax.set_title('Micropython Scope')

```

---

### Post by 23dornot23d on 2014-02-03
I will post this 18 minute video ..... because its interesting and covers a lot of ground for speeding up operations.

[http://youtu.be/-p4CVtPZoPo](http://youtu.be/-p4CVtPZoPo)

Explains how to get speed increases out of python code by using Numpy ( Numerical Python )

It also explains why it is faster to use Numpy in different situations - I am looking for speed
in operations as the one thing that makes programs seem better is when they execute quickly
and smoothly. Hope its of use to people interested in the python programming and the additional
reasoning behind why its used a lot.

Also if you want a quick look at this @ 4 : 4o explains what other speed increases can be gained
This may be interesting for real time use of data flowing through a real time display .....
[http://youtu.be/HFxn3mSp9ww](http://youtu.be/HFxn3mSp9ww)

---

### Post by linuxonbute on 2014-02-04
Interesting video, shows what can be done.
I thought I would post my code so far as someone might be interested.
Just a reminder to all reading this thread.
I wanted to use python on my laptop with a micropython board ( hereafter MPB ) - a kickstarter project I subscribed to.
I wanted to use the combination to make a simple form of oscilloscope. I have not got the MPB yet as it is about to be manufactured.
What i aim to do is write a small file to the SD card on the MPB which will tell the board how many readings to take from one of it's onboard ADC's
The board will carry out the task and then write the results to another file on the SD card. When it's finished writing it will write another small file to the SD card to confirm it has finished. Python on my laptop will copy the data file to it's own hard disc. From there the code below will process it.
```

#!/usr/bin/env python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import Button, Slider, RadioButtons
import sys
import time
with open('./rdata.txt') as f:
    for i, l in enumerate(f):
        pass
i+=1
fig, ax = plt.subplots(figsize=(17, 10))
plt.hold(False) #  <<<< Clears the plotting area when a new plot is initiated
plt.subplots_adjust(bottom=0.25, top= 0.90)


#axcolor = 'lightblue'
axcolor = 'lightgrey'
#axcolor = 'lightgoldenrodyellow'
#axcolor = 'white'
ax.set_ylabel('Voltage')
ax.set_title('Micropython Scope')
def endit(mock):
    sys.exit() 


def update(val):
    howmany = int(axvals.val)


def writefile(dummy):
    total = int(round(axvals2.val))
    print("hello" + str(total))# this is just a test to make sure function is called by my code
    # this will need to be programmed
    # to write the number of seconds to sample
    # to the SD card on the micropython (MP) board.
    # then some part of the program needs to wait for the
    #samples to be taken and written to another file on the SD card.
    # MP will read the command file and delete it then 
    # it will write the file and then write a small dummy file to signify
    # that all the data has been written.
    # The program, after it has waited say 1 second longer than the sample time
    # will read the data and do the plot.


def static_plot(dummy):
    ydata =  []
    ax1 = plt.axes ()  
    myfile = open("rdata.txt", "r")
    for myline in myfile:
        q = myline
        ydata.append(q)  
    file.close(myfile)
    fst = (int(ax1st.val))
    lst = int(axvals.val) + fst
    line, =  plt.plot (ydata[fst:lst])
    plt.draw()




def plotit(dummy):
    howmany = int(axvals.val)
    wait_time = (int(axvals1.val))
    top = i
    plt.ion() # set plot to animated
    xdata = []
    c = 0
    for a in range(0,top):
        xdata.append(a)
        c+=1


    ydata =  []
    ax1 = plt.axes ()  


    myfile = open("rdata.txt", "r")
    for myline in myfile:
        q = myline
        ydata.append(q)  
    file.close(myfile)
    c = 0
# Make plot
    line, =  plt.plot (ydata[0:howmany])
    for p in range(0, top ):
        del  ydata [ 0 ]
        line.set_xdata (np.arange ( len (ydata)))
        line.set_ydata (ydata)   # update the data
        plt.draw () # update the plot
        op='Plotting ' + str((int(p/10))*10)
        ax.set_title(op)    
        time.sleep(wait_time)




axvals = plt.axes([0.36, 0.05, 0.30, 0.025], axisbg=axcolor)
axvals = Slider(axvals, 'Points to\n display', 10, 100, valfmt='%1.0f', facecolor='lightgreen')
axvals1 = plt.axes([0.36, 0.10, 0.30, 0.025], axisbg=axcolor)
axvals1 = Slider(axvals1, 'Pause', 0, 1.0, valfmt='%1.2f', facecolor='lightgreen')
axvals2 = plt.axes([0.08, 0.15, 0.20, 0.025], axisbg=axcolor)
axvals2 = Slider(axvals2, 'Seconds\n to Record', 0.0, 60, valfmt='%1.0f', facecolor='lightgreen')
ax1st = plt.axes([0.36, 0.15, 0.30, 0.025], axisbg=axcolor)
ax1st = Slider(ax1st, '1st Point\nto display', 1, 100, valfmt='%1.0f', facecolor='lightgreen')


axplot = plt.axes([0.74, 0.05, 0.07, 0.075])
aplot = Button(axplot, 'Dynamic\nPlot')
aplot.on_clicked(plotit)


axstat = plt.axes([0.82, 0.05, 0.07, 0.075])
astat = Button(axstat, 'Static\nPlot')
astat.on_clicked(static_plot)


axout = plt.axes([0.90, 0.05, 0.07, 0.075])
aout = Button(axout, 'Exit')
aout.on_clicked(endit)


axnum = plt.axes([0.13, 0.05, 0.07, 0.075])
anum = Button(axnum, 'Start\nmeasuring')
anum.on_clicked(writefile)




plt.show()



```
Forget the comment below I found the needed information see it in the code at line 12
> 
As it stands the dynamic plot works fine and, in itself so does the static plot except I cannot, as yet find out how to clear a previous plot other than stopping and restarting the program. Say I choose to plot points 25 to 102 it works, I then choose points 41 to 95 it works but the new display overlays the first one but in a different colour and so on. Even a dynamic plot after displaying a static one displays as if it is on another layer over the top of the previous static one.
Anyone any idea what I need to do please?


---

