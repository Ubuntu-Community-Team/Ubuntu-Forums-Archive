---
title: "XLib drawing to root window"
date: 2010-02-13
forum: Programming Talk
---

### Post by richardhp on 2010-02-13
I have been extensively searching google and also reading xlib documentation for a while now and I have the following problem. Is it possible to draw a line on top of everything that is currently being displayed, without it interfering with the operation of the programs currently running? 
Basically there is an application that I want to be able to use, and while doing that have some lines being drawn over the top of that to assist me using this application.
I was hoping that this could be done by accessing the root window somehow but all of the tutorials pretty much assume that if you're doing Xlib programming that you want to create a normal window and draw stuff in that.

---

### Post by richardhp on 2010-02-13
Ok well it's ugly but I'm going to use the Shape extension library to constantly change the shape of the window, and draw on the bits I need and make the rest transparent.

---

