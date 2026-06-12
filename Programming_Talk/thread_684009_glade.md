---
title: "glade"
date: 2008-01-31
forum: Programming Talk
---

### Post by shifty2 on 2008-01-31
I'm making myself a basic text editor using python and glade and have a few questions.

Is it possible to achieve the same level of flexibility with glade as it is using pygtk? 

At the moment I'm trying to add tabs like with gedit using the notebook widget. I have got it to the point where I have 3 tabs and can have different files open in each one and save them etc. However, I would quite like to get it so a new tab opens when I open a new file, rather than going into an existing tab. I know how to do this using pygtk, but was wondering if there is a way of implementing this in glade? 

Basically is there a way of changing glade options as you run the program? I have worked out how to do simple things like change the window title but this one has me stumped.

---

### Post by luisromangz on 2008-01-31
In glade you design the GUI, but dinamic actions that changes the interface should be managed in code. If you can do it in pygtk, then there is no problem in doing so when using glade, as you have access to the pygtk controls created by glade in your program.

---

### Post by shifty2 on 2008-02-01
I realised that just after I had posted...I am now enjoying the new found power I have at my finger tips:evil:

The question I have now is how do you automatically detect when a text buffer is updated? I have done it so I can check if it is saved before I close/open a new file for example, but is there an easy way to call a function every time the buffer is modified?

---

