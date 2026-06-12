---
title: "tkinter help"
date: 2007-05-23
forum: Programming Talk
---

### Post by ninjaprawn on 2007-05-23
im trying to get tkinter to work in python, 

ive tried to compile tcl/tk from source, tcl compils fine, but tk gives loads of errors on make.

is there an easier way to get tkinter, instead of compiling??

is it available thru apt-get by any chance??

---

### Post by LaRoza on 2007-05-23
It came with Python for me, are you sure you don't already have it?

---

### Post by ninjaprawn on 2007-05-23
tkinter did, but tcl/tk didnt! i had to compile from source!

i have tried to use tkinter, but when ever i try to import anything, when i try to run it, it says there is an error, i only got a tk error, saying it is missing since i compiled tcl, but tk just wont compile!!

the readme is huge as well, i will read thru it if i have to, but i dont fancy that!

i was just hoping for an easy solution, to save me having to fix the compile!

actually, ive only installed the python interpreter! i might try and install all the stuff for python, like IDLE and such, see if that gives me the rest of it!

---

### Post by LaRoza on 2007-05-23
Python comes with Ubuntu, you can even use it on the live disk. 

TKinter comes with it also.

I do not understand your scenario, sorry.

---

### Post by WW on 2007-05-23
Strange.  In feisty, tkinter is provided by the package **python-tk**. **python-tk** depends on the packages **tcl8.4** and **tk8.4**.  So if you have tkinter installed via **python-tk**, you should also have tcl and tk.

---

### Post by ninjaprawn on 2007-05-23
tkinter isnt included with python ive just found out! i installed IDLE aswell, and now tkinter works!

i had only installed the interpreter, so i could code in python, not the ide!

thanks

---

