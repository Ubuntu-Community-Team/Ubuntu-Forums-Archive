---
title: "Python: have a program run silently/invisable and listen for keys which activate it"
date: 2008-09-30
forum: Programming Talk
---

### Post by dracule on 2008-09-30
I am currently writing a program which I need one thing for full functionality of what i want it to do.

I want it to run silently in the background (not in taskbar), until a user presses a set of keys to activate it and bring it to the front of the screen.

---

### Post by dwhitney67 on 2008-09-30
Sounds interesting!  Have you attempted to write any code for this yet?  Or are you hoping that someone else will do it for you?

On the surface, it seems that you want to develop a key-logger application.  Maybe you can Google for some advice on that topic.

---

### Post by dracule on 2008-09-30
> **dwhitney67 said:**
> Sounds interesting!  Have you attempted to write any code for this yet?  Or are you hoping that someone else will do it for you?

On the surface, it seems that you want to develop a key-logger application.  Maybe you can Google for some advice on that topic.

The only thing that I found was pyglet being able to lock out the mouse. most things i have found generally only logs the current window's key strokes. 

I think that this might have to be written in C, but I dont know C.

---

### Post by dracule on 2008-10-01
thanks for using the word "keylogger" 

i would have never associated it with that, but doing a google search for "python keylogger" led me to "pyhook" which looks like it should work.

---

