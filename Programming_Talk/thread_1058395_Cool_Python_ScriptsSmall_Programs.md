---
title: "Cool Python Scripts/Small Programs"
date: 2009-02-02
forum: Programming Talk
---

### Post by bgs100 on 2009-02-02
Okay, post your cool python scripts here. The don't have to be terribly useful, but just what you consider neat.  Here is one I made that searches google (with a bit of a cheating gui):

[PHP]#!/usr/bin/python
import os
import urllib
google = os.popen('zenity --entry --text="Enter what you want to google: " --title="google.py"').read()
google = urllib.quote(google)
os.system('firefox http://www.google.com/search?q=%s' % (google))[/PHP]

---

### Post by snova on 2009-02-02
> **bgs100 said:**
> [PHP]
google=google.split(' ')
google='+'.join(google)
[/PHP]

That should be properly escaped; merely substituting ' ' for '+' won't suffice for most non-alphabetical characters:

[php]
import urllib
google = urllib.quote(google)
[/php]

---

### Post by hamzah2096 on 2009-02-03
Simple script to use fulla (hugin bundle, barrel distortion correction). I chmod it and put some image from my camera into the same folder. I think it is quite helpful sometime.

```
#!/usr/bin/python

import os, glob, Image

pic_list = []

pic_list = glob.glob('*.JPG')
pic_list.sort()

print len(pic_list), 'images found...'
for temp in pic_list:
    print temp


cmd = 'fulla -g 0.0216776:-0.0799067:0.0566601:1 '
for temp in pic_list:
    repair = cmd + temp
    os.popen(repair).read()

```

---

### Post by Greyed on 2009-02-04
Detect if we're running in vbox.

[php]
{grey@igbuntu:~/bin} cat vbox_detect.py
#!/usr/bin/python

vbox_mac = "08:00:27"
mac_file = '/sys/class/net/eth0/address'
infile = open(mac_file, "r")
line = infile.readline()
if line.startswith(vbox_mac):
    print 'Running inside vbox'
[/php]

Later modified to include file copies via shutils to switch relevant files to the vbox versions as opposed to the real versions and vice versa.

Most notably /etc/X/xorg.conf and /etc/network/interfaces.

---

### Post by mike_g on 2009-02-04
Some code for bouncing ball physics (no friction tho) using vPython (requires python v < 2.6):
```
#!/usr/bin/python
from visual import *
import random
from math import sqrt, atan2
            
def collisions(scene):
    #check for colision against other balls
    for a in range(0, len(scene.objects)):
        for b in range(a+1, len(scene.objects)):
            dx = scene.objects[a].pos.x - scene.objects[b].pos.x
            dy = scene.objects[a].pos.y - scene.objects[b].pos.y
            #quick and dirty check to find that objects that are not going to collide
            if dx > 1: continue
            if dy > 1: continue
            #full collision check 
            distance = (dx*dx)+(dy*dy) # dont need sqrt atm as distance to check is 1
            if(distance < 1):
                diff = scene.objects[a].pos-scene.objects[b].pos
                diff = diff/sqrt(diff.x**2 +diff.y**2)    
                a_comp= diff*(scene.objects[a].velocity.x * diff.x + scene.objects[a].velocity.y * diff.y)
                b_comp= diff*(scene.objects[b].velocity.x * diff.x + scene.objects[b].velocity.y * diff.y)
                scene.objects[a].velocity= scene.objects[a].velocity - a_comp + b_comp
                scene.objects[b].velocity= scene.objects[b].velocity - b_comp + a_comp                
                #place second ball so not touching first
                mid_point= (scene.objects[a].pos + scene.objects[b].pos)/2                                
                angle = math.atan2(dy, dx)
                scene.objects[a].pos= mid_point+diff/2*1.0005
                scene.objects[b].pos= mid_point-diff/2*1.0005


    #check for collision against area bounds            
    for check in scene.objects:
        if(check.pos.x < -12):
            check.velocity = vector(abs(check.velocity.x), check.velocity.y, 0)            
        elif(check.pos.x > 12):
            check.velocity = vector(-abs(check.velocity.x), check.velocity.y, 0)            
        elif(check.pos.y < -12):
            check.velocity = vector(check.velocity.x, abs(check.velocity.y), 0)
        elif(check.pos.y > 12):
            check.velocity = vector(check.velocity.x, -abs(check.velocity.y), 0)

random.seed()
scene = display(title='Bouncy Balls', width=500, height=500, center=(0,0,0), background=(0,0,0))
scene.autoscale = 0
delta=0.1
scene.range = (-25, -25, -25)

for i in range(0, 30):
    ball = sphere(pos=(random.randint(-10, 10), random.randint(-10, 10), 0),color=(1, 1, 1),radius=0.5)
    ball.speed = float(random.randint(1, 5))/2
    ball.velocity = vector(cos(radians(i*60)), sin(radians(i*60)), 0)

while 1:
    rate(60)
    for ball in scene.objects:
        ball.pos = ball.pos + (ball.velocity*delta*ball.speed)
    collisions(scene)

```

---

### Post by crazyfuturamanoob on 2009-02-04
Here you go:
```

import os

while 1:
    os.system( "eject /dev/scd0" )

```
It makes sure you can't close your CD/DVD drive tray.

There's no way to stop it but kill python interpreter process.

---

### Post by Xcmd on 2009-02-04
A simple program I wrote for catching a bouncing ball. This utilizes Pygame... because I was bored and was trying to teach myself blitting and such. I'm sure it could be done a lot better.

```
#Catch the Ball by Xcmd
#
#A very simple game: just move the mouse and try to get the pointer over the ball.

#Import the good stuff! Read tutorials to find out why...
import sys, pygame, random
from pygame.locals import *

#Check if the fonts module loaded. If not, oosp.
if not pygame.font: print "Fonts disabled!"
pygame.init()
random.seed(pygame.time.get_ticks())

#Random numbers for some reason... hmm... what could r g b mean?
r = random.randint(0,255)
g = random.randint(0,255)
b = random.randint(0,255)

#Defining some stuff... size... speed... black?!
size = width, height = 800, 600
speed = [1, 1]
black = 0,0,0

#Setting up the screen the player sees. See how size comes from
#up there to down here? Nifty!
screen = pygame.display.set_mode(size)
pygame.display.set_caption("Catch the Ball!")

#Yes, I literally made a .png of a ball...
#I'm using convert_alpha() because I want to use the PNG's
#transparency layer instead of defining one myself. This
#also helps speed things up as far as the game goes because
#the game doesn't have to keep converting the PNG file into
#a useable graphic format. .convert() does the same thing
#but does not include transparency.
ball = pygame.image.load('ball.png').convert_alpha()

#Rects are your friends. Please read up on them.
ballrect = ball.get_rect()

#Hey, I remember r g b!
fontColor = r,g,b

#Oh honh honh! Zee font! She is Tres Arial!
font = pygame.font.SysFont("Arial Black", 25)

#winText is a surface... just in case you didn't know..
winText = font.render('You caught the ball! [Click to Play Again]', 0, fontColor)

#Look, another rect!
winRect = [0,0,0,0]

#Are we currently in a state where we've caught the ball?
caught = 0

#This is just because I wanted to show an updating surface that's
#a little more obvious than the ball zipping around.

#tix = ticks. How many ticks have passed since this was called?
tix = pygame.time.get_ticks()

#tixText = a surface!
tixText = font.render(str(tix), 0, fontColor)

#Hmm... another rect... why did I define it as nothing?
tixRect = [0,0,0,0]

#How many times did we catch the ball? Tell the user!
caughtAmt = 0
caughtText = font.render("Caught: " + str(caughtAmt), 0, fontColor)
caughtRect = [0,0,0,0]

#MAIN LOOP GO GO GO!
while 1:
	
	#Update the Tix! WOO!
	tix = pygame.time.get_ticks()
	tixText = font.render(str(tix), 0, fontColor)
	
	#Check some events. WICKED.
	for event in pygame.event.get():
		#QUITTERS QUIT, MEG!
		if event.type == pygame.QUIT:
			print "Quit event detected. Good bye!"
			sys.exit()
		if event.type == pygame.MOUSEMOTION:
			#DING FRIES ARE DONE.
			ding = event.pos
			
			#Did the mouse collide with the rect of the ball? THEN WE CAUGHT IT! YEY!
			if ballrect.collidepoint(ding) and caught != 1:
				caught = 1
				caughtAmt = caughtAmt + 1
				caughtText = font.render("Caught: " + str(caughtAmt), 0, fontColor)
		
		#Okay, so this only works when we caught the ball. If we click
		#the mouse, then we get to go again.
		if event.type == pygame.MOUSEBUTTONUP:
			if caught == 1 and event.button == 1:
				caught = 0
				speed[0] = speed[0] + 1
				speed[1] = speed[1] + 1
	
	#LIGHTNING SPEED GO! If the left-side of the ballrect is at or less
	#than the 0 position of the left-hand side of the screen OR it is
	#GREATER than or EQUAL TO the RIGHT HAND side of the screen...
	#then we need to change the direction. Same thing for top and bottom.
	ballrect = ballrect.move(speed)
	if ballrect.left < 0 or ballrect.right > width:
		speed[0] = -speed[0]
	if ballrect.top < 0 or ballrect.bottom > height:
		speed[1] = -speed[1]
	
	#fill the back of the screen with black
	screen.fill(black)
	
	#draw us a ball!
	screen.blit(ball, ballrect)
	
	#draw the surface caughtText in the upper-right
	caughtRect = screen.blit(caughtText, (600, 0))
	
	#draw the surface of the ticks counter in the upper-left
	tixRect = screen.blit(tixText, (0,0))
	
	#IF and ONLY IF we're currently in the "caught ball" state...
	#draw the winText. Oh, also prevent the ball from moving.
	if caught == 1:
		winRect = screen.blit(winText, (50, 350))
		speed = [0, 0]
	
	#What are we updating? Everything!
	updates = ballrect, tixRect, winRect, caughtRect
	pygame.display.update(updates)

```

(And, yes, I did attach the ball.png ... it's just a white ball...)

---

### Post by bgs100 on 2009-02-04
Edit: [SIZE="4"]NEVERMIND. JUST IGNORE THIS. USE IT ONLY FOR FINDING OUT WHAT THE FUTURE POSTS ARE TALKING ABOUT WHEN THEY REFER TO THIS.[/SIZE]



This nice program has been made to do your math homework:
[PHP]#!/usr/bin/python

import os
a=0
pi = 3.14
b=0
c=""
x=int(raw_input("Enter number of problems: "))		
while a != x:
	a = a+1
	b=raw_input("%i. " % (a))
	b=os.popen("awk 'BEGIN {print %s}'" % (b)).read()
	b=b[:-1]
	c = ("%s. %s\n" % (a, b)) + c
print "\n%s\n" % ('\n'.join( reversed(c.split('\n')) ))	 
[/PHP]

---

### Post by snova on 2009-02-04
> **bgs100 said:**
> [PHP]
	b=os.popen("awk 'BEGIN {print %s}'" % (b)).read()
	b=b[:-1]
[/PHP]

How about using built in tools? :)

[PHP]
      b = eval(b)
[/PHP]

---

### Post by ghostdog74 on 2009-02-04
> **bgs100 said:**
> This nice program has been made to do your math homework:
[PHP]#!/usr/bin/python

import os
a=0
pi = 3.14
b=0
c=""
x=int(raw_input("Enter number of problems: "))		
while a != x:
	a = a+1
	b=raw_input("%i. " % (a))
	b=os.popen("awk 'BEGIN {print %s}'" % (b)).read()
	b=b[:-1]
	c = ("%s. %s\n" % (a, b)) + c
print "\n%s\n" % ('\n'.join( reversed(c.split('\n')) ))	 
[/PHP]

that's not really "cool" is it? mixing different programming tools like that. If you want to use Python, do everything in Python.

---

### Post by fiddler616 on 2009-02-04
> **bgs100 said:**
> This nice program has been made to do your math homework:
[PHP]#!/usr/bin/python

import os
a=0
pi = 3.14
b=0
c=""
x=int(raw_input("Enter number of problems: "))		
while a != x:
	a = a+1
	b=raw_input("%i. " % (a))
	b=os.popen("awk 'BEGIN {print %s}'" % (b)).read()
	b=b[:-1]
	c = ("%s. %s\n" % (a, b)) + c
print "\n%s\n" % ('\n'.join( reversed(c.split('\n')) ))	 
[/PHP]
Does it do anything more exciting than this:
```

:$python uf.py
Enter number of problems: 3
1. 2+3
2. 5*3
3. What's the square root of seven?
sh: Syntax error: Unterminated quoted string


1. 5
2. 15
3. 
:$

```
?

---

### Post by bgs100 on 2009-02-06
{Removed}

---

### Post by bgs100 on 2009-02-06
> **fiddler616 said:**
> Does it do anything more exciting than this:
```

:$python uf.py
Enter number of problems: 3
1. 2+3
2. 5*3
3. What's the square root of seven?
sh: Syntax error: Unterminated quoted string


1. 5
2. 15
3. 
:$

```
?

No, but I'm about to add on to it, based on what you put in for 3...
(Like adding simple commands like sqrt)

---

### Post by Tony Flury on 2009-02-06
bgs100  : Sorry to rain on your parade, but do you intend to do natural language interpretation of mathematical problems ? I would suggest if you can do that, then you are a genius.

just think of the number of ways that the square root question could be worded - let alone the million and one other mathematical problems.

why not just log into the python interpreter, import the math module and use the print statement to execute an expression you want. This way you can of course include arbitary variables and functions - something your application will find difficult to do.

---

### Post by amar on 2009-02-06
This is a small utility attached to a large program of mine and is used to extract data from the NIST website.

Enter a chemical name/formula such as "hydrogen", "CH4", "Water", "71-43-2", etc.
The program *should* return chemical properties. 

As I said, it is part of a larger program hence, the data is not nicely formatted and displayed.

I still think it is fun.

```
import urllib
import re

def get_props(s):
    props = {}
    parse = re.compile('^<li><strong>.+:</strong>.+</li>$',re.M)
    lines = parse.findall(s)
    for line in lines:
        line = line[12:-5]
        #print line
        line = line.split(':</strong> ')
        props[line[0]]=line[1]
        #print line
    if 'Formula' in props.keys():
        props['Formula'] =props['Formula'].replace('<sub>','')
        props['Formula'] =props['Formula'].replace('</sub>','')
    parse = re.compile('<title>.+</title>')
    text = parse.search(s).group()
    props['Name']=text[7:-8].lower().replace(' ','-')
    
    parse = re.compile('<td align=\"left\">T<sub>boil</sub></td><td class=\"right-nowrap\">[\.\d]+')
    text = parse.findall(s)
    if text:
        props['Boiling Point']=text[0][63:]
    
    parse = re.compile('<td align="left">T<sub>c</sub></td><td class="right-nowrap">[\.\d]+')
    text = parse.findall(s)
    if text:
        props['Critical Temperature']=text[0][60:]
    
    parse = re.compile('<td align="left">P<sub>c</sub></td><td class="right-nowrap">[\.\d]+')
    text = parse.findall(s)
    if text:
        props['Critical Preassure']=float(text[0][60:])*10e5
    
    parse = re.compile('<li><strong>Other names:</strong>[^<>]+</li>')
    text = parse.findall(s)
    if text:
        props['Other Names']= text[0][33:-5].replace('&amp;','&')
    return props

def lookup(chemical):
    # Get a file-like object for the Python Web site's home page.
    chemical = chemical.replace(' ', '-')
    site = "http://webbook.nist.gov"
    search = "/cgi/cbook.cgi?Units=SI&cTP=on&Name="
    f = urllib.urlopen(site+search+str(chemical))
    # Read from the object, storing the page's contents in 's'.
    s = f.read()
    f.close()
    parse = re.compile('<title>.+</title>')
    title = parse.search(s).group()
    if title[7:-8] == "Name Not Found":
        return "Name not found"
    if title[7:-8] == "Search Results":
        parse = re.compile('<a href=\".+\">.+</a>')
        links = parse.findall(s)
        for link in links:
            link = link[9:-4]
            link = link.split("\">")
            if link[1].lower().replace(' ', '-') == chemical.lower():
                #print site+link[0]
                f = urllib.urlopen(site+link[0])
                s = f.read()
                f.close()
                return get_props(s)
        return "Multiple species were found"
    
    return get_props(s)

chem = raw_input("Enter a chemical: ")
props = lookup(chem)
if props =="Name not found":
    print "Chemical not found"
elif props =="Search Results":
    print "Multiple components with that name were found"
else:
    print
    for prop in props.keys():
        print prop,": ", props[prop]
    print

```

---

### Post by bgs100 on 2009-02-06
The math program just does a formula, with a nice numbered list. I was also experimenting with the os module. BTW, a new small program I and a friend just made for calculating bases 2-10 and 16.  
[PHP]#!/usr/bin/env python
a = 0
import math
pie = 0
f=''
number=int(raw_input("Enter number to convert: "))
base=int(raw_input("Enter base to convert to: "))
if base == 16:
	print hex(number)
	exit()
while pie != 1:
	x=int(math.log(number, base))
	a=number/base**x
	j=a*base**x
	number=number-j
	f=f+str(a)
	if number == 0: pie = 1
print f[/PHP]

---

### Post by fiddler616 on 2009-02-07
> **Tony Flury said:**
> 

just think of the number of ways that the square root question could be worded - let alone the million and one other mathematical problems.
To be fair, if I really wanted the square root, I would've done something like

```
3. sqrt(7)
```
I just wanted to see what happens when something a little bit interesting was inputted.

---

### Post by sujoy on 2009-02-07
i wrote a small script to find duplicate files in a given dir.

[PHP]#!/usr/bin/env python
# -*- coding: utf-8 -*-

__author__ = "Sujoy <binarycodes> (sujoy.baju@gmail.com)"
__date__   = "Tue Nov 18 01:10:06 2008"


import os
import sys
from md5sum import mymd5


class duplicateFiles(object):
    """docstring for duplicateFiles"""
    
    def __init__(self):
    	"""docstring for __init__"""
        pass

    def showDup(self, dirname):
        """
        print md5sum and the filenames of the duplicate files
        """
        m = mymd5()
        msum = 0
        fname = ""
        for md5, files in sorted(m.md5dir(dirname)):
            if msum == md5:
                print msum, fname, files
            msum = md5
            fname = files

    
if __name__ == '__main__':
    d = duplicateFiles()
    d.showDup(sys.argv[1])[/PHP]

and the md5sum generator 


[PHP]#!/usr/bin/env python
# -*- coding: utf-8 -*-

import hashlib
import os


__author__ = "Sujoy <binarycodes> (sujoy.baju@gmail.com)"
__date__   = "Tue Nov 18 01:03:35 2008"



class mymd5(object):
    """
    Re-implementation of md5sum in python
    """
    
    def __init__(self):
        """docstring for __init__"""
        pass
    
    def md5file(self, filename):
        """
        Return the hex digest of a file without loading it all into memory
        """
        fh = open(filename)
        digest = hashlib.md5()
        while 1:
            buf = fh.read(4096)
            if buf == "":
                break
            digest.update(buf)
        fh.close()
        del fh
        return digest.hexdigest()
    
    def md5list(self, files):
        for filename in files:
            try:
                return (md5file(filename), filename)
            except IOError, e:
                print >> sys.stderr, "Error on %s: %s" % (filename, e)
                return -1

    def md5dir(self,dirname):
        """
        return a pair containing filename and md5sum for each file in the dir, and files in its subdirs
        recursive process
        """
        md5_list = []
        for root, dirs, files in os.walk(dirname):
            if files != []:
                for filename in files:
                    fn = os.path.join(root,filename)
                    md5_list.append((self.md5file(fn), fn))
        return md5_list

if __name__ == "__main__":
    md5list(sys.argv[1:])[/PHP]

---

### Post by bgs100 on 2009-02-09
I might rewrite math homework program in python3, which automatically uses float math, or might try something a little interesting with the current one...

---

### Post by bgs100 on 2009-02-09
Oh, Great. I edited it quite a bit, and then didn't save #-o

---

### Post by bgs100 on 2009-02-09
{Removed}

---

### Post by UbuKunubi on 2009-02-11
This is a handy Python program i made to keep me informed of new skype chat when i have my hands full with my children.

Using Espeak to announce who has sent me what in a chat message I used the Skype4Py API to make life very easy. While I have clearly not done a lot to the original example that comes with the API it is very handy. If you see this program posted elsewhere (such as sourceforge.net) thats because I put it there.

```

# ----------------------------------------------------------------------------------------------------
#  Python / Skype4Py example that prints out chat messages
#
#  Tested with  Skype4Py version 0.9.28.5 and Skype verson 3.8.0.96

import sys
import os
import time
import Skype4Py
import random
def ndsSay(ndsWords):
    ndsIn = str(ndsWords)
    zcmd='espeak "'+ndsTalk+'"'
    print zcmd
    f=os.popen(zcmd)
    f.close()
    ndsWords=""
    ndsTalk=""
    zcmd=''
    ndsMonkey=''
        
# ----------------------------------------------------------------------------------------------------
# Fired on attachment status change. Here used to re-attach this script to Skype in case attachment is lost. Just in
#case.
def OnAttach(status):
    print 'API attachment status: ' + skype.Convert.AttachmentStatusToText(status)
    if status == Skype4Py.apiAttachAvailable:
        skype.Attach()

    if status == Skype4Py.apiAttachSuccess:
       print('***************************************')


# ----------------------------------------------------------------------------------------------------
# Fired on chat message status change. 
# Statuses can be: 'UNKNOWN' 'SENDING' 'SENT' 'RECEIVED' 'READ'        

def OnMessageStatus(Message, Status):
    if Status == 'RECEIVED':
        print(Message.FromDisplayName + ': ' + Message.Body)
        ndsSay(Message.FromDisplayName)
        ndsSay(Message.Body)

    if Status == 'READ':
        ndsMonkey = "todo"
        print(Message.FromDisplayName + ': ' + Message.Body)
        ndsSay(Message.FromDisplayName)
        ndsSay(Message.Body)

    if Status == 'SENT':
        print('Myself ' + Message.Body)


# ----------------------------------------------------------------------------------------------------
# Creating instance of Skype object, assigning handler functions and attaching to Skype.
skype = Skype4Py.Skype()
skype.OnAttachmentStatus = OnAttach
skype.OnMessageStatus = OnMessageStatus

print('***************************************')
print 'Connecting to Skype..'
skype.Attach()

# ----------------------------------------------------------------------------------------------------
# Looping until user types 'exit'
Cmd = ''
while not Cmd == 'exit':
    Cmd = raw_input('')

```

---

### Post by Bodsda on 2009-03-04
Heres a guess the number game that insults you if you get it wrong with entries in a file, separated by lines. (change the os.path.isfile() if you wish to use it)

[PHP]

#! /usr/bin/env python

import os
import random

def main():

    if os.path.isfile('/home/bod/python/code/insults.txt'):
        insults = 'yes'
        file = open('/home/bod/python/code/insults.txt', 'r')
        list = file.readlines()
    else:
        insults = "no"

    print "Welcome to guess the number\n==========================="
    print "\nI'm thinking of a number, you have to guess what it is.\n"

    num = random.randrange(100)
    guess = ""

    while guess != num:
        guess = int(raw_input("Take a guess: "))
        if guess < num:
            if insults == "yes":
                print random.choice(list)
            print "Guess higher next time\n"
        elif guess > num:
            if insults == "yes":
                print random.choice(list)
            print "Guess lower next time\n"
    print "!!***CONGRATULATIONS***!!"
    raw_input()
    if insults == "yes":
        file.close()

main()
[/PHP]

Heres a dummy run

```

Welcome to guess the number
===========================

I'm thinking of a number, you have to guess what it is.

Take a guess: 50
Wow, look at the intellectual superiority, cant even guess a number.

Guess higher next time

Take a guess: 75
Get you *** up and leave, now!

Guess higher next time

Take a guess: 90
Wow, look at the intellectual superiority, cant even guess a number.

Guess lower next time

Take a guess: 85
Get out!

Guess higher next time

Take a guess: 97
Well done muppet, you ****** up again.

Guess lower next time

Take a guess: 87
Could you be anymore stupid.

Guess higher next time

Take a guess: 88
Well done muppet, you ****** up again.

Guess higher next time

Take a guess: 89
!!***CONGRATULATIONS***!!

```

EDIT: oops sorry for the profanities in the dummy run, Ubuntu Forums, my bad

---

### Post by bgs100 on 2009-05-31
I made this small text editor a while back.  It uses wxPython, and is a bit messy in some places (it was practice with wxPython, mostly)
[PHP]#!/usr/bin/env python
import wx, os
ID_TEXT=1000

ID_NEW=100
ID_OPEN=101
ID_SAVE=102
ID_SAVEAS=103
ID_QUIT=104

ID_UNDO=200
ID_REDO=201
ID_CUT=202
ID_COPY=203
ID_PASTE=204
ID_DELETE=205
ID_SELECT_ALL=206

ID_VIEW_STATUSBAR=300

ID_ABOUT=400

ID_T_NEW=1
ID_T_OPEN=2
ID_T_SAVE=3
ID_T_UNDO=4
ID_T_REDO=5
ID_T_CUT=6
ID_T_COPY=7
ID_T_PASTE=8
class MainWindow(wx.Frame):
    def __init__(self,parent,id,title):
        wx.Frame.__init__(self,parent,wx.ID_ANY, title, size = (800,600))

        # variables
        self.modify = False
        self.undos=[]
        self.redos=[]

        self.text = wx.TextCtrl(self, ID_TEXT, style=wx.TE_MULTILINE)
        self.text.Bind(wx.EVT_TEXT, self.OnTextChanged, id=ID_TEXT)
        self.text.Bind(wx.EVT_KEY_DOWN, self.OnKeyDown)
        self.Bind(wx.EVT_CLOSE, self.OnQuit)
        self.backuptext = self.text.GetValue()
        self.statusbar = self.CreateStatusBar() #Create the statusbar

        # Setting up the "File" menu
        filemenu= wx.Menu()
        tempitem=wx.MenuItem(filemenu, ID_NEW, "&New"," Create a new document")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/Human/16x16/actions/document-new.png'))
        filemenu.AppendItem(tempitem)
        tempitem=wx.MenuItem(filemenu, ID_OPEN, "&Open"," Open a file")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/Human/16x16/actions/document-open.png'))
        filemenu.AppendItem(tempitem)
        tempitem=wx.MenuItem(filemenu, ID_SAVE, "&Save"," Save the current file")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/Human/16x16/actions/document-save.png'))
        filemenu.AppendItem(tempitem)
        tempitem=wx.MenuItem(filemenu, ID_SAVEAS, "Save &As..."," Save the current file with a different name")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/Human/16x16/actions/document-save-as.png'))
        filemenu.AppendItem(tempitem)

        filemenu.AppendSeparator()

        tempitem=wx.MenuItem(filemenu, ID_QUIT,"&Quit"," Quit the program")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/Human/16x16/actions/application-exit.png'))
        filemenu.AppendItem(tempitem)

        #Creating the "Edit" menu
        editmenu=wx.Menu()
        tempitem=wx.MenuItem(editmenu, ID_UNDO,"&Undo","Undo the last action")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/Human/16x16/actions/edit-undo.png'))
        editmenu.AppendItem(tempitem)

        tempitem=wx.MenuItem(editmenu, ID_REDO,"&Redo","Redo the last undone action")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/Human/16x16/actions/edit-redo.png'))
        editmenu.AppendItem(tempitem)

        editmenu.AppendSeparator()

        tempitem=wx.MenuItem(editmenu, ID_CUT,"Cu&t","Cut the selection")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/gnome/16x16/actions/edit-cut.png'))
        editmenu.AppendItem(tempitem)

        tempitem=wx.MenuItem(editmenu, ID_COPY,"&Copy","Copy the selection")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/gnome/16x16/actions/edit-copy.png'))
        editmenu.AppendItem(tempitem)

        tempitem=wx.MenuItem(editmenu, ID_PASTE,"&Paste","Paste the clipboard")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/gnome/16x16/actions/edit-paste.png'))
        editmenu.AppendItem(tempitem)

        tempitem=wx.MenuItem(editmenu, ID_DELETE,"&Delete","Delete the selected text")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/gnome/16x16/actions/edit-delete.png'))
        editmenu.AppendItem(tempitem)

        editmenu.AppendSeparator()

        tempitem=wx.MenuItem(editmenu, ID_SELECT_ALL,"Select &All","Select the entire document")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/gnome/16x16/actions/edit-select-all.png'))
        editmenu.AppendItem(tempitem)

        # Setting up the "View" menu
        viewmenu=wx.Menu()
        self.statusbaritem=wx.MenuItem(viewmenu, ID_VIEW_STATUSBAR,"&Statusbar","Show or hide the statusbar in the current window")
        self.statusbaritem.SetCheckable(True)

        viewmenu.AppendItem(self.statusbaritem)
        self.statusbaritem.Check()
        
        # Setting up the "Help" menu
        helpmenu=wx.Menu()
        tempitem=wx.MenuItem(helpmenu, ID_ABOUT, "&About"," About this application")
        tempitem.SetBitmap(wx.Bitmap('/usr/share/icons/Human/16x16/actions/gtk-about.png'))
        helpmenu.AppendItem(tempitem)
        # Creating the menubar.
        menuBar = wx.MenuBar()
        menuBar.Append(filemenu, "&File") # Adding the "filemenu" to the MenuBar
        menuBar.Append(editmenu, "&Edit") # Adding the "editmenu" to the MenuBar
        menuBar.Append(viewmenu, "&View") # Adding the "viewmenu" to the MenuBar
        menuBar.Append(helpmenu, "&Help") # Adding the "helpmenu" to the MenuBar
        self.SetMenuBar(menuBar)  # Adding the MenuBar to the Frame content.
        wx.EVT_MENU(self, ID_NEW, self.OnNew)
        wx.EVT_MENU(self, ID_OPEN, self.OnOpen)
        wx.EVT_MENU(self, ID_SAVE, self.OnSave)
        wx.EVT_MENU(self, ID_SAVEAS, self.OnSaveAs)
        wx.EVT_MENU(self, ID_QUIT, self.OnQuit)

        wx.EVT_MENU(self, ID_UNDO, self.OnUndo)
        wx.EVT_MENU(self, ID_REDO, self.OnRedo)
        wx.EVT_MENU(self, ID_CUT, self.OnCut)
        wx.EVT_MENU(self, ID_COPY, self.OnCopy)
        wx.EVT_MENU(self, ID_PASTE, self.OnPaste)
        wx.EVT_MENU(self, ID_DELETE, self.OnDelete)
        wx.EVT_MENU(self, ID_SELECT_ALL, self.OnSelectAll)

        wx.EVT_MENU(self, ID_VIEW_STATUSBAR, self.ToggleStatusBar)

        wx.EVT_MENU(self, ID_ABOUT, self.OnAbout)

        #Make the toolbar
        toolbar = wx.ToolBar(self, -1, style=wx.TB_HORIZONTAL | wx.NO_BORDER)
        toolbar.AddSimpleTool(ID_T_NEW, wx.Image('/usr/share/icons/Human/24x24/actions/document-new.png',  wx.BITMAP_TYPE_PNG).ConvertToBitmap(), 'Create a new document', '')
        toolbar.AddSimpleTool(ID_T_OPEN, wx.Image('/usr/share/icons/Human/24x24/actions/document-open.png',  wx.BITMAP_TYPE_PNG).ConvertToBitmap(), 'Open a file', '')
        toolbar.AddSimpleTool(ID_T_SAVE, wx.Image('/usr/share/icons/Human/24x24/actions/document-save.png',  wx.BITMAP_TYPE_PNG).ConvertToBitmap(), 'Save the current file', '')
        toolbar.AddSeparator()
        toolbar.AddSimpleTool(ID_T_UNDO, wx.Image('/usr/share/icons/Human/24x24/actions/edit-undo.png',  wx.BITMAP_TYPE_PNG).ConvertToBitmap(), 'Undo the last action', '')
        toolbar.AddSimpleTool(ID_T_REDO, wx.Image('/usr/share/icons/Human/24x24/actions/edit-redo.png',  wx.BITMAP_TYPE_PNG).ConvertToBitmap(), 'Redo the last undone action', '')
        toolbar.AddSeparator()
        toolbar.AddSimpleTool(ID_T_CUT, wx.Image('/usr/share/icons/gnome/24x24/actions/edit-cut.png',  wx.BITMAP_TYPE_PNG).ConvertToBitmap(), 'Cut the selection', '')
        toolbar.AddSimpleTool(ID_T_COPY, wx.Image('/usr/share/icons/gnome/24x24/actions/edit-copy.png',  wx.BITMAP_TYPE_PNG).ConvertToBitmap(), 'Copy the selection', '')
        toolbar.AddSimpleTool(ID_T_PASTE, wx.Image('/usr/share/icons/gnome/24x24/actions/edit-paste.png',  wx.BITMAP_TYPE_PNG).ConvertToBitmap(), 'Paste the clipboard', '')
        self.Bind(wx.EVT_TOOL, self.OnNew, id=ID_T_NEW)
        self.Bind(wx.EVT_TOOL, self.OnOpen, id=ID_T_OPEN)
        self.Bind(wx.EVT_TOOL, self.OnSave, id=ID_T_SAVE)

        self.Bind(wx.EVT_TOOL, self.OnUndo, id=ID_T_UNDO)
        self.Bind(wx.EVT_TOOL, self.OnRedo, id=ID_T_REDO)
        self.Bind(wx.EVT_TOOL, self.OnCut, id=ID_T_CUT)
        self.Bind(wx.EVT_TOOL, self.OnCopy, id=ID_T_COPY)
        self.Bind(wx.EVT_TOOL, self.OnPaste, id=ID_T_PASTE)
        self.SetToolBar(toolbar)
        self.Show(True)
    def OnNew(self, e):
        self.filename, self.dirname = 'New File',''
        self.text.Clear()
        self.SetTitle("IsMEdit - "+self.filename)
    def OnOpen(self, e):
        """ Open a file"""
        self.dirname = ''
        dlg = wx.FileDialog(self, "Choose a file", self.dirname, "", "*.*", wx.OPEN)
        if dlg.ShowModal() == wx.ID_OK:
            self.filename=dlg.GetFilename()
            self.dirname=dlg.GetDirectory()
            f=open(os.path.join(self.dirname,self.filename),'r')
            self.text.SetValue(f.read())
            f.close()
            self.SetTitle("IsMEdit - "+self.filename)
        dlg.Destroy()
    def OnSaveAs(self, e):
        self.dirname = ''
        dlg = wx.FileDialog(self, "Choose a file", self.dirname, "", "*.*", wx.SAVE)
        if dlg.ShowModal() == wx.ID_OK:
            self.filename=dlg.GetFilename()
            self.dirname=dlg.GetDirectory()
            f=open(os.path.join(self.dirname,self.filename),'w')
            f.write(self.text.GetValue().encode('utf8'))
            f.close()
        dlg.Destroy()
        self.SetTitle("IsMEdit - "+self.filename)
    def OnSave(self, e):
        try:
            f=open(os.path.join(self.dirname,self.filename),'w')
            f.write(self.text.GetValue().encode('utf8'))
        except AttributeError: self.OnSaveAs(e)
    def OnQuit(self, e):
        if self.modify:
            dlg = wx.MessageDialog(self, 'Save before exiting?', '', wx.YES_NO | wx.YES_DEFAULT | wx.CANCEL |  wx.ICON_QUESTION)
            val = dlg.ShowModal()
            if val == wx.ID_YES:
                self.OnSave(e)
                self.Destroy()
            elif val == wx.ID_CANCEL:
                dlg.Destroy()
            else:
                self.Destroy()
        else:
            self.Destroy()
    def OnUndo(self, e):
        place=self.text.GetInsertionPoint()
        self.redos.append(self.text.GetValue())
        self.text.SetValue(self.undos[len(self.undos)-1])
        self.text.SetInsertionPoint(place)
        self.undos=self.undos[:-1]
        if len(self.redos) >= 30: self.redos=self.redos[1:]
    def OnRedo(self, e):
        place=self.text.GetInsertionPoint()
        self.text.SetValue(self.redos[len(self.redos)-1])
        self.text.SetInsertionPoint(place)
        self.redos=self.redos[:-1]
    def OnCut(self, e):
        self.text.Cut()
    def OnCopy(self, e):
        self.text.Copy()
    def OnPaste(self, e):
        self.text.Paste()
    def OnDelete(self, e):
        frm, to = self.text.GetSelection()
        self.text.Remove(frm, to)
    def OnSelectAll(self, e):
        self.text.SelectAll()
    def ToggleStatusBar(self, e):
        if self.statusbar.IsShown():
            self.statusbar.Hide()
            self.statusbaritem.Check(False)
        else:
            self.statusbar.Show()
            self.statusbaritem.Check()

    def OnAbout(self,e):
        d= wx.MessageDialog(self, "(I)an's (M)ini (Edit)or\nA simple editor written in wxPython","About IsMEdit", wx.OK) # Create a message dialog box
        d.ShowModal() # Shows it
        d.Destroy() # finally destroy it when finished.
    def OnTextChanged(self, e):
        self.modify=True
        e.Skip()
    def OnKeyDown(self, e):
        keycode = e.GetKeyCode()
        self.undos.append(self.text.GetValue())
        if len(self.undos) >= 30: self.undos=self.undos[1:]
        e.Skip()

app = wx.PySimpleApp()
frame = MainWindow(None, -1, "IsMEdit - New File")
frame.SetIcon(wx.Icon('/usr/share/icons/gnome/16x16/apps/accessories-text-editor.png', wx.BITMAP_TYPE_PNG))
app.MainLoop()[/PHP]

---

### Post by benj1 on 2009-05-31
in a similar vein to the OPs google utility, heres minefor displaying google searches in a terminal.

```
#!/usr/bin/env python


import sys
from optparse import OptionParser
parser = OptionParser(
	version=" %prog V0.1 Ben Holroyd",   
	description = "%prog - google results in the terminal.",
	usage = "%prog [-vr] [--view] [--results][--help] [--version]")
parser.add_option("-r","--results",action="store",type = "int",dest="results",help="display specified number of results, default is 10." )
parser.add_option("-v","--view",action="store",type = "int",dest="view",help="view page by index number." )    
(options,args) = parser.parse_args()
    
if options.view != None: #opens selected entry in browser, then exit
	file = open("/tmp/google",'r')
	text = file.readlines()	
	counter = 1
	for lines in text:
		if counter == options.view: 
			from subprocess import call
			call("w3m %s" % lines, shell = True)
			sys.exit(0)
		counter += 1
    		
    		    
print "loading..."
option = ""
for arg in args: option += arg+"+"
if len(option) == 0: parser.error("please enter a search term")

from urllib import FancyURLopener
class MyOpener(FancyURLopener): version = '' #google doesn't like the user agent so send blank it blank
try:   
	s = MyOpener().open('http://www.google.com/search?q=%s'% option).read()
except IOError:
	print 'could not connect to google, check your connection'
	return 1
import re
dict = {}
entry = re.split('<li class=g><h3 class=r>',s) #split page by results
entry = entry[1:]                              #get rid of first bit
counter = 1
for s in entry:
	s = s.replace(''',"'")                 #hack hack hack
	s = s.replace('&amp;',"&")
	s = s.replace('&middot;',"\302\267")
	s = s.replace('&quot;','"')
	s = s.replace('&lt;','<')
	s = s.replace('&gt;','>')
	s = s.replace('&#26412;','\346\234\254')
	s = s.replace('&#26085;','\346\227\245')
	s = s.replace('&nbsp;',' ')

    	
	entry = re.split('<br>',s)# gets rid of last bits #cached and similar pages  etc
	s=entry[0]
    	
	a = s.find("<a href")     #get web address
	b = s.find("</a>")
	address = s[a:b]
	title = s[a:b]            # get title
	a = address.find('"')
	address = address[a+1:]
	b = address.find('"')
	address = address[:b]
    
	b = s.find("</a>")
	s = s[b:]                  #clean up main description string 
    
	s = re.sub('<.*?>','',s)
	title = re.sub('<.*?>','',title)    	                        
    	
	print "\033[34;04m[%d] %s\033[00;00m" % (counter , title)
	print s
	print "\033[32;01m%s\033[00;00m" % address
	print "-----------------------------------------------------------"
	dict[counter] = address
	if options.results == counter: break
	counter += 1
file = open("/tmp/google",'w')
for entries in range(1,len(dict)+1): file.write(dict[entries]+'\n')
file.close()
```

---

### Post by ando1991 on 2010-08-09
Want to talk to someone, but all your friends are busy? Getter is always available.
```

#!/usr/bin/python -tt
# Have a conversation with a PandaBot AI
# Author A.Roots

import urllib, urllib2
import sys
from xml.dom import minidom
from xml.sax.saxutils import unescape

def main():
  
  human_input = raw_input('You: ')
  if human_input == 'exit':
    sys.exit(0)
  
  base_url = 'http://www.pandorabots.com/pandora/talk-xml'
  data = urllib.urlencode([('botid', 'ebbf27804e3458c5'), ('input', human_input)])
  
  # Submit POST data and download response XML
  req = urllib2.Request(base_url)
  fd = urllib2.urlopen(req, data)
  
  # Take Bot's response out of XML
  xmlFile = fd.read()
  dom = minidom.parseString(xmlFile)
  objektid = dom.getElementsByTagName('that')
  bot_response = objektid[0].toxml()
  bot_response = bot_response[6:]
  bot_response = bot_response[:-7]
  # Some nasty unescaping
  bot_response = unescape(bot_response, {"&apos;": "'", "&quot;": '"'})
  
  print 'Getter:',str(bot_response)
  
  # Repeat until terminated
  while 1:
    main()

if __name__ == '__main__':
  print 'Hi. You can now talk to Getter. Type "exit" when done.'
  main()

```

---

### Post by HoKaze on 2010-08-09
You know in movies and other media computer terminals are supposed to be green text on black and all the output comes out as if typed one line at a time? I looked for a while for a simple program that could output files or user input in this manner (and of course, my terminal is green on black with a matrix font :3) so I wrote this:

```
#!/usr/bin/env python
# Prints input one character at a time 
from time import *
import os, sys

char_start = 0
char_end = 1
string = sys.stdin.read() #use standard input to allow more than 1 line

if len(sys.argv) > 1: #checks for command line arguments
    delay = float( sys.argv[1] ) #uses argument as delay time

else:
    delay = 0.05

strlength = len(string)+1

while char_end <= strlength:
    printchar = string[char_start:char_end]
    sys.stdout.write(printchar)
    sys.stdout.flush()
    sleep(delay) #delay time between characters
    char_end += 1
    char_start += 1

exit
```

There's probably a much simpler way of doing that and I've been an idiot but hey, I eventually managed to write it and in time got rid of some bugs and made it more cross-platform (the original code was...an awful ugly hack far worse than this).
It accepts standard input from the user across multiple lines until you escape with control+d, then it prints the string one character at a time, typewriter-style. Naturally I made it so that you can pipe other commands into it and by specifying a value like 0.01 as an argument the delay can be altered.

It's not much but I thought it was cool and I'm proud of it :P

---

### Post by anthro398 on 2010-08-09
This creates a dialog box that allows me to select the mode to sync my work documents from a computer, e.g. laptop, to my desktop.  So, I go to meetings, take notes, take the computer home and work on code, and can sync changes easily using rsync over ssh.  I have a launcher on my panel.  At the end of the meeting or when I'm done working on something, I just click the launcher and sync the directories.  Kind of like a local Dropbox.

```

#!/usr/bin/env python



from commands import getstatusoutput
from sys import exit

# set local variables
remotehost = 'work'
localdir = '/home/xxx/Documents/work'
remotedir = '/home/xxx/Documents/work'
user = 'xxx'

# set zenity dialog text
dialog = """zenity --title='Laptop Sync' --text='Select backup mode' --list  --radiolist  --column "Select" --column "Mode" True 'Safe Sync' FALSE 'Delete Laptop Files' FALSE 'Delete Server Files'"""
mode = getstatusoutput(dialog)



# backup mode: bidirectional rsync, no deletion of files
if mode[1] == 'Safe Sync':
	com = """rsync -auzvv --copy-links --human-readable --update -e "ssh -l %s" %s:%s/ %s  && rsync -auzv --human-readable --update -e "ssh -l %s" %s/ %s:%s""" % (user, remotehost, remotedir, localdir, user, localdir, remotehost, remotedir)


# backup mode: unidirectional server to laptop, delete laptop files that don't exist on server	
elif mode[1] == 'Delete Laptop Files':
	com = """rsync -auzvv --copy-links --human-readable --update --delete-during -e "ssh -l %s" %s@%s:%s/ %s""" % (user, user, remotehost, remotedir, localdir)	


# backup mode: unidirectional laptop to server, delete server files that don't exist on laptop
elif mode[1] == 'Delete Server Files':
	com = 'rsync -auzvv --copy-links --human-readable --update --delete-during -e "ssh -l %s" %s/ %s:%s' % (user, localdir, remotehost, remotedir)

# error state, something wrong with zenity dialog passing variables to this script
else: 
	getstatusoutput("""zenity --warning --title="Backup Error!" --text="Error! Exiting..." """)
	exit()

print '\n\nExecuting command: ', com
status = getstatusoutput(com)
print '\n\nRsync output: ', status[1]

# display status of backup, offer to show output
if status[0] == 0:
	view = getstatusoutput("""zenity --question --title='Sync Successful' --text 'Laptop sync completed.  View rsync output?' """)
else:
	view = getstatusoutput("""zenity --question --title='Sync Failed' --text 'Laptop sync failed.  View rsync output?' """)


# if display of output is selected, display output
if view[0] == 0:
	com = 'zenity --error --title="Rsync Output" --text="%s"' %  (status[1])
	getstatusoutput(com)
print 'done'

```

---

### Post by teryret on 2010-08-10
So my math teacher gave me a weird homework problem that I didn't understand until your little eval program helped me, the problem was

"import os

while 1:
    os.system( "eject /dev/scd0" )"

;)

---

### Post by bendib on 2011-10-04
This thread deserves to be resurrected... :^)
Really lazy-made IRC client implemented with telnetlib...
```

#!/usr/bin/env python
"""Dr00l python IRC Client v0.60, by bendib."""
import telnetlib, os, time, threading, sys
dr00lver = 'v0.60'
def initprompt():
  # print initial version.
  print 'Dr00l IRC Client for python ' + dr00lver
  #define global variables.
  global hostprompt
  hostprompt = raw_input('Hostname: ')
  global portprompt
  portprompt = raw_input('Port number: ')
  global nickprompt
  nickprompt = raw_input('Nick: ')
  global userprompt
  userprompt = raw_input('Username: ')
  global rnameprompt
  rnameprompt = raw_input('Real name: ')
  global chanprompt1
  chanprompt1 = raw_input('First channel to join (type none for none): ')
  global chanprompt2
  chanprompt2 = raw_input('Second channel to join (type none for none): ')
  irc_main()
def irc_main():
  # define te, used throughout the program and make it global.
  global te
  te = telnetlib.Telnet(hostprompt, portprompt)
  # print startup message and login to server.
  print 'Starting up...'
  te.write('user ' + userprompt + ' 8 * :' + rnameprompt + '\n')
  te.write('nick ' + nickprompt + '\n')
  if not chanprompt1 == 'none':
   te.write('join ' + chanprompt1 + '\n')
  if not chanprompt2 == 'none':
   te.write('join ' + chanprompt2 + '\n')
  # start threads
  pingthread = threading.Thread(target=pingserver)
  pingthread.start()
  readirct = threading.Thread(target=readirc)
  readirct.start()
  dr00lgreett = threading.Thread(target=dr00lgreet)
  dr00lgreett.start()
  # set up commands
  while True:
   readcommands = raw_input('')
   # msg command
   if readcommands == 'msg':
    recipient = raw_input('Recipient or channel? ')
    if not recipient == 'cancel':
     imessage = raw_input('Message? ')
     te.write('privmsg ' + recipient + ' :' + imessage + '\n')
     print 'Message sent.'
   # me command
   if readcommands == 'me':
    recipient = raw_input('Recipient or channel? ')
    if not recipient == 'cancel':
     imessage = raw_input('Thing to say? ')
     te.write('privmsg ' + recipient + ' :\x01ACTION ' + imessage + '\x01\n')
     print 'Message sent.'
   # quit command
   if readcommands == 'quit':
    print 'Shutting down.'
    te.close()
    os._exit(0)
   # join command
   if readcommands == 'join':
    channame = raw_input('Channel name? ')
    if not channame == 'cancel':
     te.write('join ' + channame + '\n')
   # part command
   if readcommands == 'part':
    channame = raw_input('Channel name? ')
    if not channame == 'cancel':
     te.write('part ' + channame + '\n')
   # mode command
   if readcommands == 'mode':
    channame = raw_input('Enter mode command: ')
    if not channame == 'cancel':
     te.write('mode ' + channame + '\n')
   # invite command
   if readcommands == 'invite':
    nickname = raw_input('Nick name? ')
    if not nickname == 'cancel': 
     channame = raw_input('Channel name? ')
     te.write('invite ' + nickname + ' ' + channame + '\n')
     print 'Invite sent.'
   # kick command
   if readcommands == 'kick':
    nickname = raw_input('Nick name? ')
    if not nickname == 'cancel':
     channame = raw_input('Channel name? ')
     te.write('kick' + channame + ' ' + nickname + '\n')
   # topic command
   if readcommands == 'topic':
    topicname = raw_input('Topic? ')
    if not topicname == 'cancel':
     channame = raw_input('Channel name? ')
     te.write('topic ' + channame + ' :' + topicname + '\n')
   # nickserv command, for authenticating to nickserv.
   if readcommands == 'nickserv':
    pwdname = raw_input('Password? ')
    if not pwdname == 'cancel':
     te.write('privmsg nickserv :identify ' + pwdname + '\n')
   # nick command, to change nick.
   if readcommands == 'nick':
    newnick = raw_input('New nick? ')
    if not newnick == 'cancel':
     te.write('nick ' + newnick + '\n')
   # names command
   if readcommands == 'names':
    nargs = raw_input('Arguments for names command? (type none for none): ')
    te.write('names')
    if not nargs == 'none':
     te.write(' ' + nargs)
    te.write('\n')
   # help command
   if readcommands == 'help':
    print '~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~'
    print 'Commands are: help, read, msg, me, join, part, nick,'
    print 'nickserv, mode, invite, kick, topic, quit, dr00lver.'
    print '~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~'
   # dr00lver command
   if readcommands == 'dr00lver':
    print '~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~'
    print 'dr00l python IRC Client ' + dr00lver
    print '~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~'

def pingserver():
 # set up thread to ping server
 while True:
  te.write('ping ' + hostprompt + '\n')
  time.sleep(60)

def readirc():
 # set up thread to read IRC.
  time.sleep(1)
  while True:
   sys.stdout.write(te.read_very_eager())
   time.sleep(0.5)

def dr00lgreet():
 #launch one time thread for initial message.
 time.sleep(5.0)
 print '~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~'
 print 'DR00L MESSAGE: Welcome to dr00l ' + dr00lver + '! Type "help" for help. Don\'t do "msg foo foo", but just "msg" and follow through. Same with all commands.'
 print '~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~'
# start the client now that everything is in order.
initprompt()


```

---

### Post by pr3zident on 2011-10-04
Simple Python Program to do simple task in Ubuntu 

```
from os import system

def showoptions():
    print "SYSTEM ADMIN PANEL 3.0"
    print ""
    print "1 - Quit"
    print "2 - Delete a file"
    print "3 - Show disk info"
    print "4 - List Dir"
    print "5 - Update"
    print "6 - uname"
    print "7 - Gedit"
    print "8 - Install"
    print "9 - Start Up Applications"
    print "10 - Add Repository"
    print "11 - Shutdown"
    print "12 - Top"
    print "13 - pwd"
    print "14 - Wget"
    print "15 - PYTHON"
    print "100 - MSG"
    print ""

# 2     
def deletefile():
    filename = raw_input("Enter Filename: ")
    result = system("rm -vr " + filename)
    if (result != 0):
        print "Error Deleting file!"
    else:
        print "File deleted OK"
        print "Press enter...."
        raw_input()

# 3    
def diskinfo():
    system("df -h")
    print "Press Enter..."
    raw_input()

# 4    
def listopt():
    system("ls -haF")
    print "Press Enter"
    raw_input()

# 5  
def update():
    system("apt-get update && apt-get upgrade") 
    print "Press Enter"
    raw_input()
    
# 6   
def cpuinfo():
    system("uname -a")
    print "Press Enter"
    raw_input()

# 7       
def gedit():
    system("nohup gedit&") 
    print "Press Enter"
    raw_input

# 8    
def install():
    filename = raw_input("Enter Filename: ")
    result = system("apt-get install " + filename + " > install.txt")
    if (result != 0):
        print "Application not found"
    else:
        print "File Downloaded"
        print "Press Enter"
        raw_input

# 9 
def startup():
    system("nohup gnome-session-properties") 
    print "Press Enter"
    raw_input

# 10
def repo():
    repolist = raw_input("Please Enter Repository: ")
    result = system("add-apt-repository ppa:" + repolist + " > repository.txt")
    if (result != 0):
        print "Repository Not added"
    else:    
        print "Repository Added"
        print "Press Enter..."
        raw_input()

# 11
def reboot():
    system("shutdown -h now")

# 12     
def top():
    system("top")
    print "Press Enter"
    raw_input()

# 13 
def pwd():
    system("pwd")
    print "Press Enter"
    raw_input()   

# 14 wget
def wget():
    web = raw_input("Enter Website: ")
    result = system("wget " + web)
    if (result != 0):
        print "Website Not Downloaded"
    else:
        print "Website Downloaded" 
        print "Press Enter"
        raw_input()   
#15 py
def py():   
    python = raw_input("PYTHON: ")
    result = system("python " + python + " > PYTHON PROBLEM")
    if (result != 0):
        print "CODE CAN'T BE RAN"
    else:
        print "Code Running"
        print "Press Enter"
        raw_input()
    
# 100  
def msg():
    print "BACK UP EVERYTHING BEFORE YOU LOSE EVERYTHING" 
    raw_input()
       
x = 0 

while (x != 1):
    system("clear")
    showoptions()
    x = input("Enter your choice: ")
    
    if (x == 2):
        deletefile()
    if (x == 3):
        diskinfo()
    if (x == 4):
        listopt()
    if (x == 5):
        update()
    if (x == 6):
        cpuinfo()
    if (x == 7):
        gedit()
    if (x == 8):
        install()
    if (x == 9):
        startup()
    if (x == 10):
        repo()
    if (x == 11):
        reboot()
    if (x == 12):
        top()
    if (x == 13):
        pwd()
    if (x == 14):
        wget()
    if (x == 15):
        py()
    if (x == 100):
        msg()
        
print "Program ended."
```

---

### Post by juancarlospaco on 2011-10-04
^ I like this one, but maybe Fabric can simplify the script...

---

### Post by pr3zident on 2011-10-06
> **juancarlospaco said:**
> ^ I like this one, but maybe Fabric can simplify the script...

Thank you what's fabric ?

---

### Post by coolmonk7 on 2011-10-24
Here is a cool program i wrote!
```
from Tkinter import *
import random

canvas = Canvas(width=600, height=600, bg='white')   
canvas.pack(expand=YES, fill=BOTH)                  

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
    
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(500,500,500,500, width=10, fill='yellow')

canvas.create_line(500,500,500,500, width=10, fill='orange')

canvas.create_line(500,500,500,500, width=10, fill='black')

canvas.create_line(500,500,500,500, width=10, fill='black')

canvas.create_line(500,500,500,500, width=10, fill='yellow')

canvas.create_line(500,500,500,500, width=10, fill='orange')

canvas.create_line(500,500,500,500, width=10, fill='black')

canvas.create_line(500,500,500,500, width=10, fill='black')

canvas.create_line(500,500,500,500, width=10, fill='yellow')

canvas.create_line(500,500,500,500, width=10, fill='orange')

canvas.create_line(500,500,500,500, width=10, fill='black')

canvas.create_line(500,500,500,500, width=10, fill='black')

canvas.create_line(500,500,500,500, width=10, fill='yellow')

canvas.create_line(500,500,500,500, width=10, fill='orange')

canvas.create_line(500,500,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(600,600,500,500, width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='red')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='blue')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='orange')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='black')

canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='brown')



mainloop()
                      

 


```

---

### Post by coolmonk7 on 2011-10-24
Here is another version of that program!
([COLOR="Red"]MAKE SURE YOU GO ON FULL SCREEN![/COLOR] 
```
from Tkinter import *
import random

canvas = Canvas(width=500, height=500, bg='white')  
canvas.pack(expand=YES, fill=BOTH)                

canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='blue')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='pink')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=1, fill='red')
canvas.create_line(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=10, fill='green')

mainloop()


```

---

### Post by coolmonk7 on 2011-10-24
Here is another version!:lolflag:
(open in full screen)
```
from Tkinter import *
import random

canvas = Canvas(width=1000, height=1000, bg='white')  
canvas.pack(expand=YES, fill=BOTH)                

canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='yellow')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='blue')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='black')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='red')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='pink')
canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill='purple')
```

---

### Post by mushy365 on 2011-10-24
This is a gui python script i wrote that allows you to sync two folders. I did it for making my downloaded music, backup onto my hard drive so the files match.


[IMG]http://i52.tinypic.com/1z73dco.png[/IMG]


```

#!/usr/bin/env python

#imports
import os
import sys
import gtk
import glob
import pygtk
import shutil
import ConfigParser
import threading
pygtk.require('2.0')

class Base:
    
    quitsync = False
    srcDirExists = True
    dstDirExists = True
    showFoldersOnly = False
    showHiddenFilesandFolders = False
    
    
    def updatesearch(self,widget):
        self.scanSourceDir(None)
        self.scanDestDir(None)


    def toggle_folders_only(self,widget):
        if self.showFoldersOnly == True:
           self.showFoldersOnly = False

        else:
           self.showFoldersOnly = True
        
        print "ShowFoldersOnly Value = " + str(self.showFoldersOnly)
        self.scanSourceDir(None)
        self.scanDestDir(None)

    def destroy(self,widget,data=None):
        gtk.main_quit() 
    
    def deleteall(self,widget):
        self.dstDir = self.destTxtBox.get_text()
        #now we need to delete all files from this folder.
        self.num_of_files = 0
        self.numnow = 0
        os.chdir(self.dstDir)
        self.ffiles = glob.glob("*.*")

        for f in self.ffiles:
            while gtk.events_pending():
               gtk.main_iteration()
            self.num_of_files = self.num_of_files + 1


        for f in self.ffiles:
            while gtk.events_pending():
               gtk.main_iteration()   
            self.numnow = self.numnow + 1
            self.notice = "Deleting File: " + f + "(" + str(self.numnow) + " of " + str(self.num_of_files) + ")"
            self.pbar.set_text(self.notice)
            #self.pbar.pulse()
            self.percent = float(self.numnow) / float(self.num_of_files)
            self.pbar.set_fraction(self.percent) 

            os.remove(self.dstDir + "/" + f) 
            self.scanDestDir(None) 
        self.pbar.set_text("All files deleted")
        self.pbar.set_fraction(1) 
    
    def get_icon_from_ext(self,ext,filename,path):
        #trys to find an icon, if not returns self.fileIcon
        if ext == "mp3":
           return self.mp3Icon

        elif ext == "m4a":
           return self.musicIcon

        elif ext == "txt":
           return self.txtIcon

        elif ext == "jar":
           return self.exeIcon

        elif ext == "tar":
           return self.exeIcon

        elif ext == "avi":
           return self.videoIcon

        elif ext == "png" or ext == "jpg" or ext == "jpeg" or ext == "gif":
           #self.imgIcon = gtk.gdk.pixbuf_new_from_file_at_size(path + "/" + filename,24,24)
           #print "image :" + path + "/" + filename
           return self.jpgIcon
        else:
           return self.fileIcon
 
    def scanSourceDir(self,widget):
        self.srcDir = self.sourceTxtBox.get_text()
        self.searchstring = self.topnavSearchTxtBox.get_text().lower()

        self.sourcestore.clear()
        if os.path.isdir(self.srcDir):
           self.srcDirExists = True
           #os.chdir(self.srcDir)
           #self.srcfiles = glob.glob("*.*")
        
           for f in os.listdir(self.srcDir):
               if os.path.isdir(os.path.join(self.srcDir,f)):
                  #print os.path.join(self.srcDir,f)
                  if not f.startswith("."):
                     self.sourcestore.append([self.dirIcon, f, "Folder"])
               else:
                 
                  self.fileparts = str(f).split(".")
                  if len(self.fileparts) < 2:
                     self.filext = "File"
                  else:
                     self.filext =str(self.fileparts[-1]).lower()
                  
                  #this will stop the hidden folders being appended - can add a bool option for this later to turn on and off
                  if not f.startswith(".") and self.showFoldersOnly == False and f.lower().find(self.searchstring) != -1:
                     #test if its a file type we recognise to add custom icon
                        self.sourcestore.append([self.get_icon_from_ext(self.filext,f,self.srcDir), f, "File"])
 
        else:
           self.sourcestore.append([self.errIcon,"Not Valid Directory.", "Error"])
           self.srcDirExists = False
           print "No valid directoy"
       

    def scanDestDir(self,widget):
        #self.dstDir = self.destTxtBox.get_text()
        self.searchstring = self.topnavSearchTxtBox.get_text().lower()
        ##check for / at end
        #if not self.dstDir.endswith("/"):
        self.dstDir = self.destTxtBox.get_text()
           #self.destTxtBox.set_text(self.dstDir)

        self.deststore.clear()
        if os.path.isdir(self.dstDir):
           self.dstDirExists = True
           #os.chdir(self.dstDir)
           #self.dstfiles = glob.glob("*.*")
        
           for f in os.listdir(self.dstDir):
               if os.path.isdir(os.path.join(self.dstDir,f)):
                  #print os.path.join(self.dstDir,f)
                  if not f.startswith("."):
                     self.deststore.append([self.dirIcon, f, "Folder"])
               else:
                  
                  self.fileparts = str(f).split(".")
                  if len(self.fileparts) < 2:
                     self.filext = "File"
                  else:
                     self.filext =str(self.fileparts[-1]).lower()
                  #this will stop the hidden folders being appended - can add a bool option for this later to turn on and off
                  if not f.startswith(".") and self.showFoldersOnly == False and f.lower().find(self.searchstring) != -1:
                     self.deststore.append([self.get_icon_from_ext(self.filext,f,self.dstDir), f , "File"])

        else:
            self.deststore.append([self.errIcon, "Not Valid Directory", "Error"])
            self.srcDirExists = False
            print "No valid directoy"

    def stopSyncFolders(self, widget):
        self.quitsync = True  
        
    

    def syncFolders(self, widget):
        #print "in sync folders stopsync = " + str(self.quitsync)

        #need to check if srcDirExists and dstDirExist = True before trying to sync
        #TODO

        if self.sourceTxtBox.get_text().endswith("/"):
               self.sourceTxtBox.set_text(self.sourceTextBox.get_text()[:-1])

        if self.destTxtBox.get_text().endswith("/"):
               self.destTxtBox.set_text(self.destTextBox.get_text()[:-1])

        self.sd = self.sourceTxtBox.get_text()
        self.dd = self.destTxtBox.get_text()
        
        
        self.files_to_copy = 0
        self.files_copied = 0
        
        os.chdir(self.sd)
        self.ffiles = glob.glob("*.*")
        for f in self.ffiles:
            if not os.path.exists(self.dd + "/" + f):
               self.files_to_copy = self.files_to_copy + 1
        for f in self.ffiles:

           while gtk.events_pending():
              gtk.main_iteration()
           if not os.path.exists(self.dd + "/" + f):
              self.files_copied = self.files_copied + 1
              self.notice = "Copying file " + str(self.files_copied) + " of " + str(self.files_to_copy) + "( " + f + ")"
              self.pbar.set_text(self.notice)
              shutil.copyfile(self.sd + "/" + f, self.dd + "/" + f)
              self.deststore.append([self.okIcon ,f, "Copied"])
              self.percent = float(self.files_copied) / float(self.files_to_copy)
              
              self.pbar.set_fraction(self.percent)  
              
              if self.quitsync == True:
                self.pbar.set_text("Cancelled") 
                self.pbar.set_fraction(0)
                break

        os.chdir(self.dd)
        self.ffiles = glob.glob("*.*")

        for f in self.ffiles:
            while gtk.events_pending():
               gtk.main_iteration()
            if not os.path.exists(self.sd + "/" + f):
               self.notice = "Deleting File: " + f
               self.pbar.set_text(self.notice)
               self.pbar.pulse()
               os.remove(self.dd + "/" + f)
               print "** File Removed :" + f 

            if self.quitsync == True:
                self.pbar.set_text("Cancelled") 
                self.pbar.set_fraction(0.0)
                self.quitsync = False
                break        

        if self.quitsync == False:
           self.pbar.set_text("Sync completed")
           self.pbar.set_fraction(1.0)

    def get_icon(self, name):
        theme = gtk.icon_theme_get_default()
        return theme.load_icon(name, 24, 0)    

    def on_src_activated(self, widget,row,col): 
        model = widget.get_model()
        path =  model[row][1] 
        #print "Path =" + path
        type = model[row][2]

        if not type == "Folder":
            return
            
        #self.srcDir = self.srcDir + os.path.sep + path
        if self.sourceTxtBox.get_text() == "/":
           self.sourceTxtBox.set_text("/" + path)
        else: 
           self.sourceTxtBox.set_text(self.sourceTxtBox.get_text() + "/"+ path)
        self.scanSourceDir(None)

    def on_dst_activated(self, widget,row,col): 
        model = widget.get_model()
        path =  model[row][1] 
        #print "Path =" + path
        type = model[row][2]

        if not type == "Folder":
            return
            
        #self.srcDir = self.srcDir + os.path.sep + path
        if self.destTxtBox.get_text() == "/":
           self.destTxtBox.set_text("/" + path)
        else: 
           self.destTxtBox.set_text(self.destTxtBox.get_text() + "/"+ path)
        self.scanDestDir(None)

    def __init__(self):
        #lets start developing
        #lets make main background window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_position(gtk.WIN_POS_CENTER)
        self.window.set_size_request(800,800)
        self.window.set_title("Pysync - Folder Sync")

        #create the vertical and horizontal boxes
        self.mainvbox = gtk.VBox()
        self.topnav = gtk.HBox()
        self.topaddrbox = gtk.HBox()
        self.topscrollwindowbox = gtk.HBox()
        self.bottomaddrbox = gtk.HBox()
        self.bottomscrollwindowbox = gtk.HBox()
        self.optionbar = gtk.HBox()
        self.actionbar = gtk.HBox()
        
        #set the sizes of the hboxs
        self.topnav.set_size_request(800,30)
        self.topaddrbox.set_size_request(800,30)
        #self.topscrollwindowbox.set_size_request(800,300)
        self.bottomaddrbox.set_size_request(800,30)
        #self.bottomscrollwindowbox.set_size_request(800,300)
        self.optionbar.set_size_request(800,30)
        self.actionbar.set_size_request(800,30)

        #currentworkingidr
        self.cwd = os.getcwd()
        print self.cwd
        ##########GET ICONS############
        self.fileIcon = self.get_icon(gtk.STOCK_FILE)
        self.dirIcon = self.get_icon(gtk.STOCK_DIRECTORY)
        self.errIcon = self.get_icon(gtk.STOCK_DIALOG_ERROR)
        self.okIcon = self.get_icon(gtk.STOCK_YES)
        self.musicIcon = gtk.gdk.pixbuf_new_from_file_at_size("/usr/share/icons/Humanity/mimes/24/application-ogg.svg",24,24)
        self.exeIcon = gtk.gdk.pixbuf_new_from_file_at_size("/usr/share/icons/Humanity/mimes/24/application-x-ace.svg",24,24)
        self.txtIcon = gtk.gdk.pixbuf_new_from_file_at_size("/usr/share/icons/Humanity/mimes/24/text-plain.svg",24,24)
        self.videoIcon = gtk.gdk.pixbuf_new_from_file_at_size("/usr/share/icons/Humanity/mimes/24/media-video.svg",24,24)
        self.searchIcon = gtk.gdk.pixbuf_new_from_file_at_size("/usr/share/icons/Humanity/actions/24/edit-find.svg",24,24)
        self.imgIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.cwd +"/icons/jpg.jpeg",24,24)
        self.jpgIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.cwd +"/icons/jpg.jpeg",24,24)
        self.mp3Icon = gtk.gdk.pixbuf_new_from_file_at_size(self.cwd +"/icons/mp3.png",24,24)
        ##########GET ICONS END########




        #########CREATE LISTSTORES###########
        #change back to str fixfix
        self.sourcestore = gtk.ListStore(gtk.gdk.Pixbuf,str,str)
        self.deststore = gtk.ListStore(gtk.gdk.Pixbuf,str,str)
        #########CREATE LISTSTORES END########


        #########CREATE TREEVIEWS#######
        #creating the treeview object to put in src scroll window
        self.srctreeView = gtk.TreeView(self.sourcestore)
        self.srctreeView.connect("row-activated", self.on_src_activated)
        self.srctreeView.set_rules_hint(True)

        #creating the treeview object to put in src scroll window
        self.dsttreeView = gtk.TreeView(self.deststore)
        self.dsttreeView.connect("row-activated", self.on_dst_activated)
        self.dsttreeView.set_rules_hint(True)
        #########CREATE TREEVIEWS END#########


        #######CREATE COLUMNS#########
         #creating the columns to be listen in the scroll window
        self.srcrendererText = gtk.CellRendererText()
        self.srcimgrend = gtk.CellRendererPixbuf()
        ##fixfix cange back to text not pixbuf

        self.srcimgcolumn = gtk.TreeViewColumn(" ", self.srcimgrend, pixbuf = 0)
        self.srcimgcolumn.set_fixed_width(100)

        self.srccolumn = gtk.TreeViewColumn("Name", self.srcrendererText, text=1)
        self.srccolumn.set_sort_column_id(1)
        self.srccolumn.set_min_width(650)

        self.srctypecolumn = gtk.TreeViewColumn("Type", self.srcrendererText, text=2)
        self.srctypecolumn.set_sort_column_id(2)   
        
        self.srctreeView.append_column(self.srcimgcolumn)
        self.srctreeView.append_column(self.srccolumn)
        self.srctreeView.append_column(self.srctypecolumn)

        #creating the columns to be listen in the scroll window
        self.dstrendererText = gtk.CellRendererText()
        self.dstimgrend = gtk.CellRendererPixbuf()
        ##fixfix cange back to text not pixbuf

        self.dstimgcolumn = gtk.TreeViewColumn(" ", self.dstimgrend, pixbuf=0)
        #self.dstimgcolumn.set_sort_column_id(0)
        self.dstimgcolumn.set_fixed_width(100)

        self.dstcolumn = gtk.TreeViewColumn("Name", self.dstrendererText, text=1)
        self.dstcolumn.set_sort_column_id(1)  
        self.dstcolumn.set_min_width(650)

        self.dsttypecolumn = gtk.TreeViewColumn("Type", self.dstrendererText, text=2)
        self.dsttypecolumn.set_sort_column_id(2)    
        
        self.dsttreeView.append_column(self.dstimgcolumn)
        self.dsttreeView.append_column(self.dstcolumn)
        self.dsttreeView.append_column(self.dsttypecolumn)
        ######CREATE COLUMNS END#######







        #Create the widgets to go in boxes

        #topnav img textbox
        self.tnlabel = gtk.Label("Search: ")
        self.topnavSearchTxtBox = gtk.Entry()
        self.topnavSearchTxtBox.set_size_request(400,30)
        self.topnavSearchTxtBox.connect("changed",self.updatesearch)

        #Fist topaddrbox  /label/textbox/button
        self.sourceLabel = gtk.Label("Source:")
        self.sourceTxtBox = gtk.Entry()
        self.sourceTxtBox.set_size_request(600,30)
        self.sourceTxtBox.set_text("/")
        self.sourceButton = gtk.Button("Set Folder")
        self.sourceButton.connect("clicked",self.scanSourceDir)
        

        #second topscrollwindowbox  scroll window and list
        self.ssw = gtk.ScrolledWindow()
        self.ssw.set_shadow_type(gtk.SHADOW_ETCHED_IN)
        self.ssw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        self.ssw.add(self.srctreeView)

        #third bottomaddrbox /label/textbox/button
        self.destLabel = gtk.Label("Dest:")
        self.destTxtBox = gtk.Entry()
        self.destTxtBox.set_size_request(600,30)
        self.destTxtBox.set_text("/")
        self.destButton = gtk.Button("Set Folder")
        self.destButton.connect("clicked",self.scanDestDir)


        #scan paths for files
        self.scanSourceDir(None)
        self.scanDestDir(None)
      
        #fourth bottomscrollwindowbox /scroll window and list
        self.dsw = gtk.ScrolledWindow()
        self.dsw.set_shadow_type(gtk.SHADOW_ETCHED_IN)
        self.dsw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        self.dsw.add(self.dsttreeView)

        #optionbar
        self.checkFoldersOnly = gtk.CheckButton("Display folders only")
        self.checkFoldersOnly.connect("toggled",self.toggle_folders_only)

        #fifth actionbar
        self.syncButton = gtk.Button("Sync Folders")
        self.syncButton.connect("clicked",self.syncFolders)
        self.stopsyncButton = gtk.Button("Stop sync")
        self.stopsyncButton.connect("clicked",self.stopSyncFolders)
        self.deleteAllButton = gtk.Button("Delete all")
        self.deleteAllButton.connect("clicked",self.deleteall)
        
        self.pbar = gtk.ProgressBar()
        self.pbar.set_size_request(500,30)
        
        
        #now add all widgets to boxes.
        #topnav
        self.tnimg = gtk.image_new_from_pixbuf(self.searchIcon)
        self.topnav.pack_start(self.tnlabel,False,False,5)
        self.topnav.pack_start(self.topnavSearchTxtBox,False,False,5)
        self.topnav.pack_start(self.tnimg,False,False,5)

        #topaddrbox
        self.topaddrbox.pack_start(self.sourceLabel,False,False,5)
        self.topaddrbox.pack_start(self.sourceTxtBox,False,False,5)
        self.topaddrbox.pack_start(self.sourceButton,False,False,5)

        #bottomaddrbox
        self.bottomaddrbox.pack_start(self.destLabel,False,False,5)
        self.bottomaddrbox.pack_start(self.destTxtBox,False,False,5)
        self.bottomaddrbox.pack_start(self.destButton,False,False,5)

        #topscrollwindowbox
        self.topscrollwindowbox.pack_start(self.ssw)

        #bottomscrollwindowbox
        self.bottomscrollwindowbox.pack_start(self.dsw)

        #actionbar
        self.actionbar.pack_start(self.pbar,False,False,5)
        self.actionbar.pack_start(self.syncButton,False,False,5)
        self.actionbar.pack_start(self.stopsyncButton,False,False,5)
        self.actionbar.pack_start(self.deleteAllButton,False,False,5)

        #optionbar
        self.optionbar.pack_start(self.checkFoldersOnly,False,False,5)

        #add final horizontal boxes to vertical box
        self.mainvbox.pack_start(self.topnav,False,False,5)
        self.mainvbox.pack_start(self.topaddrbox,False,False,5)
        self.mainvbox.pack_start(self.topscrollwindowbox)
        self.mainvbox.pack_start(self.bottomaddrbox,False,False,5)
        self.mainvbox.pack_start(self.bottomscrollwindowbox)
        self.mainvbox.pack_start(self.optionbar,False,False,5)
        self.mainvbox.pack_start(self.actionbar,False,False,5)

        
        #add the mainvbox to windown and display it
        self.window.add(self.mainvbox)
        self.window.show_all()
        self.window.connect("destroy",self.destroy)

    def main(self):
        gtk.main()


if __name__ == "__main__":
    base = Base()
    base.main()

```

---

### Post by CoffeeRain on 2011-10-25
Here's a little script that writes out each character onto another terminal, as if it was being typed on that one. Paired with SSH, it could make some funny results. The ttys000 can be replaced with whichever one you want.

```
import termios, fcntl, sys, os
fd = sys.stdin.fileno()

oldterm = termios.tcgetattr(fd)
newattr = termios.tcgetattr(fd)
newattr[3] = newattr[3] & ~termios.ICANON & ~termios.ECHO
termios.tcsetattr(fd, termios.TCSANOW, newattr)

oldflags = fcntl.fcntl(fd, fcntl.F_GETFL)
fcntl.fcntl(fd, fcntl.F_SETFL, oldflags | os.O_NONBLOCK)

try:
    while 1:
        try:
            c = sys.stdin.read(1)
	    if c==' ':
              sys.stdout.write(' ')
              os.system("printf ' ' > /dev/ttys000")
            elif c=='\n':
              sys.stdout.write('\n')
              os.system("printf '\n' > /dev/ttys000")
            sys.stdout.write(c)
            os.system("printf " + c +" > /dev/ttys000")
        except IOError: pass
finally:
    termios.tcsetattr(fd, termios.TCSAFLUSH, oldterm)
    fcntl.fcntl(fd, fcntl.F_SETFL, oldflags)
```

---

### Post by lykwydchykyn on 2011-10-25
This script returns the number of available updates.  I wrote it for my conky setup:

```


#!/usr/bin/python

import apt

c = apt.cache.Cache()
c.open()
num = [x for x in c if x.is_upgradable]

print(len(num))

```

---

### Post by lykwydchykyn on 2011-10-25
> **coolmonk7 said:**
> Here is another version!:lolflag:
(open in full screen)

Please please please... we have looping constructs for a reason!

```
from Tkinter import *
import random

canvas = Canvas(width=1000, height=1000, bg='white')  
canvas.pack(expand=YES, fill=BOTH)                

colors = ['yellow', 'blue', 'black', 'red', 'pink', 'purple']

for i in range(10):
    for mycolor in colors:
        canvas.create_oval(0,random.randrange(0,1000,2),random.randrange(0,1000,2),random.randrange(0,1000,2), width=random.randrange(0,10,1), fill=mycolor)

```

---

### Post by pr3zident on 2011-10-29
> **juancarlospaco said:**
> ^ I like this one, but maybe Fabric can simplify the script...

This scripts performs administration task using ssh also performs some local task. 

```

#######################################     
#   Adminstration Task                #
#   Verison 1.0.0                     #
#   prezident <pr3zident@ubuntuforums>#
#   Modified OCT 28, 2011 2:26am      #
#   Modified OCT 29, 2011 1:26am      # 
####################################### 

#!/usr/bin/env python
from fabric.api import *

###### Connect to ssh server ########
env.hosts = ['xxx.xxx.x.xxx']
env.user = 'JOHN'
#env.password = 'DOE' # YOU DON'T HAVE TO PUT A PASSWRD HERE 
######################################

###############################################
#ADMIN TASK THAT YOU WANT TO RUN ON SSH SERVER# 
###############################################

#1  w 
def w():
    run('w')
    
#2  uptime
def uptime():	
    run("uptime")

#3 
def repo():
    repolist = raw_input("Please Enter Repository: ")
    result = system("sudo add-apt-repository ppa: " + repolist)
    if (result != 0):
        print "Repository Not added"
    else:    
        print "Repository Added"

#4    
def install():
    filename = raw_input("Enter Filename: ")
    result = system("sudo apt-get install " + filename)
    if (result != 0):
        print "Application not found"
    else:
        print "File Downloaded"

#5  update
def update():
    run("sudo apt-get update && sudo apt-get upgrade")

#6  autoclean
def autoclean():
    run("sudo apt-get autoclean")

#7  diskinfo  
def diskinfo():
    run("df -h")

#8  du
def du():
    run('du -sh')

#9  free 
def free():
    run('free -m')

#10  dpkg
def dpkg():
    run("dpkg -l")
     
#11  top
def top():
    run("top")

#12 ps    
def ps():
    run("ps -e")

#13
def kill():
    run("echo Enter PID to KILL: ; read id ; ps -e | grep $id; kill $id &>/dev/null ; echo")

#14 mount	
def mount():
    run('mount')
##umount

#15 usb 
def usb():
    run("lsusb")
    
#16 iwconfig
def iwconfig():
    run("sudo iwconfig")

#17 if
def ifconfig():
    run("sudo ifconfig")

#18 backup - how ever you back up your cpu then run your backup script mine is called drive
#def backup():
#    run("drive")

#19 reboot
def reboot():
    run('sudo reboot')

#20 shutdown
def shutdown():
    run("sudo init 0")

#################
##  log files  ##
#################

#21 dmesg
def dmesg():
    run("cat /var/log/dmesg > /home/`whoami`/Desktop/dmesg.txt;scp /home/`whoami`/Desktop/dmesg.txt name@host:/home/you/wherever")

#22 auth.log
def auth():
    run("cat /var/log/auth.log > /home/`whoami`/Desktop/auth.log.txt;scp /home/`whoami`/Desktop/auth.log.txt name@host:/home/you/wherever")

#23 boot.log
def boot():
    run("cat /var/log/boot.log > /home/`whoami`/Desktop/boot.txt;scp /home/`whoami`/Desktop/boot.txt name@host:/home/you/wherever")

#24 syslog 
def syslog():
    run("cat /var/log/syslog > /home/`whoami`/Desktop/syslog.txt;scp /home/`whoami`/Desktop/syslog.txt name@host:/home/you/wherever")
    
#25 bootstrap
def boot():
    run("cat /var/log/bootstrap.log > /home/`whoami`/Desktop/boot.txt;scp /home/`whoami`/Desktop/boot.txt name@host:/home/you/wherever")


################
#MISC.COMMANDS## 
################  
#26 date
def date():
    local("date && cal")

#27 ls
def ls():
    run("ls") 

#28 pwd 
#def pwd():
#    local("pwd")
    
#29 uname 
def uname():
    run("uname -a")     

#30 who
def who():
    run('whoami')  
   
#31 delete
def delete():
    filename = raw_input("Enter Filename: ")
    result = system("rm -v " + filename)
    if (result != 0):
        print "Error Deleting file!"
    else:
        print "File deleted OK"

#32 wget
def wget(): 
    run("wget: ")        

##############
# Cool Message
##############

#100  
def msg():
    local("echo BACK UP EVERYTHING BEFORE YOU LOSE EVERYTHING") 


```

if anybody have any ideas or add-ons let me know thanx

---

