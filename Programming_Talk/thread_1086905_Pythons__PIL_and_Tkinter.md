---
title: "Pythons  PIL and Tkinter"
date: 2009-03-04
forum: Programming Talk
---

### Post by ulysses-31 on 2009-03-04
Hi there i wonder if anyone can help me

I am faily new at python and dont fully understand how it works.
I am trying to make a GUI which modifies images

I have created two small python programs

1st program is an image modifier which just takes an image from the directory and darkens it for this i used PIL.

2nd program is a Simple Gui which just has a some text and a button for this i used tkinter.

What i have been trying to do is make it so that the button calls the image modifier program and apply the changes to the image.

But i don't know how any ideas

Kind Regards
Ulysses

Ps Sorry if my question is unclear. If you need the files i am working with i have attached them

---

### Post by stevescripts on 2009-03-04
Don't have time right now to d/load and look at your code...

The tk canvas widget (and therefore tkinter) only have support for limited types of images (see [http://www.tcl.tk/man/tcl8.4/TkCmd/photo.htm#M47](http://www.tcl.tk/man/tcl8.4/TkCmd/photo.htm#M47)) - what kind of image are you wanting to display?

There is an Image extension available for tcl/tk - but I dont know for sure if it is usable from tkinter.
Steve

---

### Post by stevescripts on 2009-03-04
PIL appears (from a quick google search) to enable tkinter to handle other types of images also.

You may find this useful:  [http://codeidol.com/python/python3/A-Tkinter-Tour,-Part-1/Viewing-and-Processing-Images-with-PIL/](http://codeidol.com/python/python3/A-Tkinter-Tour,-Part-1/Viewing-and-Processing-Images-with-PIL/)

In short, you need to configure the button widget to call your func(p) function -   self.btnDisplay = Button(self, text="Mod Image", command=func(p)), or something along those lines.

You dont need 2 separate scripts - one seems better to me in this case (as you dont have to deal with calling a function that exists in one script, from the other script).

Hope this helps a bit - no more time available today to play with this.

Steve

---

