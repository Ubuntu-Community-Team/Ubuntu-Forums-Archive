---
title: "What programming framework to draw a line on top level window"
date: 2012-01-14
forum: Programming Talk
---

### Post by TimKraemer on 2012-01-14
Hello!

I've come across a GUI programming problem, where I need some help:

I need a library which enables me to **draw multiple lines on top of an active fullscreen window**. 

The background story is that my program runs in the background while I'm giving a presentation with my laptop. The program tracks a laserpointer on the projected slides via webcam. Upon giving a specific command this programm will plot a line on the projected slides, such that it looks like I can 'draw' on my slides with my laser pointer. The presentation has to remain active window in order to be able to move forward and backward with the slides.

This application in fullscreen will most likely be LibreOffice or any application to display PDF's. 

In more practical terms: I have to create a fullscreen transparent window on top of all other windows, without being in focus and without capturing input.

So far I've considered Qt and Xlib (both to which I'm totally new), but could not find a way to implement my idea.

May be you can help: What options do I have in general?

---

### Post by TimKraemer on 2012-01-14
I just made a breakthrough:

I had some success in creating a fullscreen, 'always-on-top', transparent widget, that opens without activating. This is almost what I want. 

The only thing missing here is forwarding any input (e.g. mouse) to the application for presentation. Input by keyboard/usb-devices is already forwarded to the presentation as long as the widget does not get the focus. Can I prevent a widget from ever getting focused?

---

