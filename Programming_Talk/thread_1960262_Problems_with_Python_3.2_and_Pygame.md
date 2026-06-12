---
title: "Problems with Python 3.2 and Pygame"
date: 2012-04-17
forum: Programming Talk
---

### Post by blackhex666 on 2012-04-17
So i tried installing pygame using this tutorial:
```
Okay, so I struggled for about an hour trying to get &#8216; pygame &#8216; run  with Python 3 on my ubuntu 11.04 machine, so I decided to write a post  about it.
By default, Ubuntu ships with Python 2.7 installed, so pygame gets installed with python 2.7.
To install it with python3, do the following:
1. Open up the terminal and type the following code:
sudo apt-get install python3-dev libsdl-image1.2-dev libsdl-mixer1.2-dev  libsdl-ttf2.0-dev libsdl1.2-dev libsmpeg-dev python-numpy subversion  libportmidi-dev
2. Then once all libraries are downloaded and installed, type:
svn co svn://seul.org/svn/pygame/trunk pygame
 cd pygame
 python3 setup.py build
 sudo python3 setup.py install
 3. That&#8217;s all! You can now run pygame with python3.
 I have also updated this on the pygame website, so that no one falls into this trouble again! [IMG]http://s1.wp.com/wp-includes/images/smilies/icon_wink.gif?m=1336659725g[/IMG]

```And now when i trie to import it i get this:
```
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    import pygame
  File "/usr/local/lib/python3.2/dist-packages/pygame/__init__.py", line 95, in <module>
    from pygame.base import *
ImportError: /usr/local/lib/python3.2/dist-packages/pygame/base.cpython-32mu.so: undefined symbol: PyCObject_Check
```

Please HELP !!

---

### Post by blackhex666 on 2012-04-18
bump...no wan can help me??

---

### Post by yoanar on 2012-04-18
Go to line 123 in the setup.py file and change raw_input() to just input(), that was the error i had when i tried installing it (because the function was chaged in Python3, causing many compitability problems with python mainly in terminal apps). 
And you should probably get pygame from [http://www.pygame.org/download.shtml](http://www.pygame.org/download.shtml) instead.
 
Message me back if this doesn't work.

---

### Post by WolfRage on 2012-10-07
Thanks, yoanar, line 123 is the problem, curious why they still have not fixed that.
Solved Pygame on Python 3.2 Import Error.

---

### Post by finch.joseph on 2013-01-08
I have tried all the suggestions here.   I changed raw_input to input.   I've downloaded all the dependencies.   I have compiled and built pygame over and over but it never works.    Can someopne please help me get pygame 3.2 installed.  

Thanks,
Joe

---

### Post by micahpage on 2013-01-10
@
[finch.joseph]("http://ubuntuforums.org/member.php?u=1481257")

I have pygame for python3.x installed on my desktop, but i redid my laptop and when i tried to install pygame for python3 i had a heck of time doing it. I also installed the python3-dev and sdl dependencies and removed the raw_input() to input(), but kept getting the error the OP stated.

So i checked my desktop and found that i was using pygame 1.9.2 pre and not 1.9.1. So with 1.9.2 pre i got it to to work on my laptop, which was a fresh install of ubuntu.

Here was my process:

0) downloaded 1.9.2 pre which took me a bit just to find: [https://launchpad.net/debian/experimental/+source/pygame/1.9.2~pre~r3144-1/+files/pygame_1.9.2~pre~r3144.orig.tar.gz](https://launchpad.net/debian/experimental/+source/pygame/1.9.2~pre~r3144-1/+files/pygame_1.9.2~pre~r3144.orig.tar.gz)

1) i had to remove pygame from python3's dist-packages, the pygame directory and the egg-info from 1.9.1
```
/usr/local/lib/python3.2/dist-packages
```2) installed these (which i know some are non relavent, but i found it and just copied and pasted and installed anyways) 
```
sudo apt-get install python3-dev libsdl-image1.2-dev libsdl-mixer1.2-dev  libsdl-ttf2.0-dev libsdl1.2-dev libsmpeg-dev python-numpy subversion  libportmidi-dev
```3) then 
```
sudo python3 setup.py install
```which by the way : no sudo and it will run and execute without errors, but you will still not be able to import pygame, so sudo it

this is the python version i am using with this also:
```
metulburr@ubuntu:~$ python3 --version
Python 3.2.3
```


you will also get a message saying that some of the dependencies will not run, but i havent had a problem with anything for the past year on the desktop trying to run others programs or writing code myself with anything.

At this point import pygame was successful on my laptop

---

