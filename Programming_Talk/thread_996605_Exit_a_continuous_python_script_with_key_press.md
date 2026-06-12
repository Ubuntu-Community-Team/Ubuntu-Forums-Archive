---
title: "Exit a continuous python script with key press?"
date: 2008-11-29
forum: Programming Talk
---

### Post by OldGregory on 2008-11-29
So I have this python script which looks roughly like this:
[php]while 1:
    proc = subprocess.Popen('sudo iwlist wlan0 scan', shell=True, stdout=subprocess.PIPE, )
    results = proc.communicate()[0].split('\n')

    # do stuff with wireless scan results

[/php]

How would I monitor for a keypress, like the escape button, so I can exit the while loop?

---

### Post by mentallaxative on 2008-11-29
You could enclose it within a try-except block, where except catches KeyboardInterrupt. The key to press will have to be Ctrl-C though.

---

### Post by crazyfuturamanoob on 2008-11-29
Perhaps you could write a small C module which get's the keypresses from X11, and then sends exit signal to the python app?

I once wrote an application with C, which uses X11 to make fake key presses. Works probably the other way around too.

---

### Post by Majorix on 2008-11-29
Why not use the EOF combination?

---

### Post by OldGregory on 2008-11-29
> **mentallaxative said:**
> You could enclose it within a try-except block, where except catches KeyboardInterrupt. The key to press will have to be Ctrl-C though.

Sounds kinda hacky...8).  

That'll work fine for now, but I was just hoping there was a module I could use.

---

### Post by unutbu on 2008-11-29
If you are okay with using Ctrl-C to break, 
then there is the signal module which you could use to catch the SIGINT signal:

[PHP]#!/usr/bin/env python
# See http://www.linuxjournal.com/article/3946 listing #3

import signal 
import sys
import subprocess

def signal_handler(signal, frame):
    print 'You pressed Ctrl-C!'
    sys.exit(0)
signal.signal(signal.SIGINT, signal_handler)
print 'Press Ctrl-C to stop'
while 1:
    proc = subprocess.Popen('sudo iwlist wlan0 scan', shell=True, stdout=subprocess.PIPE, )
    results = proc.communicate()[0].split('\n')
    # do stuff with wireless scan results  [/PHP]

---

