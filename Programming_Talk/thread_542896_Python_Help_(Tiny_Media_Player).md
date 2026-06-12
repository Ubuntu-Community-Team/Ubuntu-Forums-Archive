---
title: "Python Help (Tiny Media Player)"
date: 2007-09-04
forum: Programming Talk
---

### Post by bobbocanfly on 2007-09-04
I decided to give Python a go as it is being properly hyped up and everyone here recommends it to people who arent amazing at programming yet.

Because i cant find one that meets what i want i decided my first task would be to build a tiny MP3 player that can run in one of the TTY windows alongside Irssi and just be out of the way,

Started working on it earlier today and so far have some basic functionality. The code i have at the moment is:

```
# uPlayer 0.1.0
# Tiny CLI Python Media Player
# Created 03/09/2007
# Based on library from PyGame

import sys
import pygame
import os

if os.path.exists("/tmp/uPlayer"):
   f = open("/tmp/uPlayer/STATUS", "w")
   f.write("IDLE")
   f.close
else:
   os.mkdir("/tmp/uPlayer")
   f = open("/tmp/uPlayer/STATUS", "w")
   f.write("IDLE")
   f.close
   
fname = 0

for arg in sys.argv:
   f = arg
   if f != "main.py":
      fname = f
      break

if fname == "-p":
   f = open("/tmp/uPlayer/STATUS", "w")
   f.write("PAUSE")
   f.close
   sys.exit()
elif fname == "-h":
   print "uPlayer - 0.1.0"
   print "Usage:"
   print "uPlayer <filename> : Plays File"
   print "uPlayer -p : Pauses/Resumes Playing"
   print "uPlayer -x : Exits uPlayer"
   print "uPlayer -h : Displays this help information"
   sys.exit()
else:
   f = open("/tmp/uPlayer/STATUS", "w")
   f.write("PLAYING")
   f.close
   
if os.path.exists(fname):
   print "Loading File"
else:
   print "Could not find file"
   sys.exit()
playing = 1
while playing == 1:
   pygame.init()
   interrupt = 0
   music = pygame.mixer.music.load(fname)
   pygame.mixer.music.play()
   while interrupt == 0:
      f = open("/tmp/uPlayer/STATUS", "w")
      #contents = f.read()
      contents = "hello"
      if contents == "PAUSE":
         pygame.mixer.music.pause()
         #f.write("PLAYING")
         #f.close()
         break
      else:
         continue
      break

```

Yes i know, the first thing you are going to say is, why the hell are you using PyGame for a MP3 Player? The answer because i couldnt find another library that was as easy as that. Does anyone have any suggestions for a different MP3 playing library? 

Also that code wont end properly (It stays in the nested While loop) and the only way of currently stopping it is to kill Python, which isnt really what i want!

The nested While loop is used for reading the status file whch will be written to by uPlayer -p which can be run from another terminal window and will pause/resume the app.

Does anyone have any suggestions on how to make it better?

---

### Post by nanotube on 2007-09-04
well, of course it doesn't exit your while loops - because it doesn't seem like playing is ever set = 0, or interrupt is ever set = 1. 

also, you might consider using the optparse library rather than manually parsing them yourself. :)

and also, why not just use mpg123, e.g., as a terminal music player, instead of rolling your own solution (unless you are just doing it for practice)...

---

### Post by bobbocanfly on 2007-09-04
Im working on the exiting problem which will set interrupt to 1 when the song finishes

I am doing this partly for practise but the fact that ill find it useful made me want to do it even more. Thanks for the heads up on mpg123 though!

---

### Post by pmasiar on 2007-09-04
If you are looking for a set of fun training task, look no further than PythonChallenge.com! 33 increasingly more difficult tasks, will keep you busy for couple of months and you will learn all corners of Python. Forums with hints available.

For more traditional workout, see training tasks in wiki in my sig.

---

