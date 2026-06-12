---
title: "PROJECT: Media Player!"
date: 2012-10-18
forum: Programming Talk
---

### Post by sunnypt on 2012-10-18
OK! so after spending some time getting familiar with basic shell scripting i wanna learn how to do a bit more complex stuff, not just them Hello World scripts.
May be going way over my head here, but i would like to start building my own media player. doesn't need to be fancy, but i have no idea how to do it so i wanna start learning.
Does anyone have any resources i can check, or simple guides from where i can start from?  thx guys!

---

### Post by Lisiano on 2012-10-18
In my opinion, you might be going over your head. Start lower, like a simple shell game, like Russian Roulette (If you aim to create cli-only stuff) or try to make a basic GUI which just shows the current time (If you are trying to make GUI stuff).

Also, you might want to take a look at some source code for other applications, like [mplayer](http://www.mplayerhq.hu/) or [xeyes](http://xeyes.sourcearchive.com/documentation/1.0.1/xeyes_8c-source.html).

I'm no programmer btw.

---

### Post by papibe on 2012-10-18
Moved to **Programming Talk**.

---

### Post by SledgeHammer_999 on 2012-10-18
If you want to make a media player you have to choose another programming language. Something like C, C++ or python. You will also want to learn some GUI programming. [Gtk+](www.gtk.org) or [Qt](www.qt-project.org) basically. Both GUI frameworks have bindings for python( and Gtk+ has for C++ too). Also you will need to learn to use [GStreamer](http://gstreamer.freedesktop.org/) for media playback.
A good tutorial for gstreamer beginners is this->[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html)

But I think this will be too much for you since you are still an amateur and you can't even code a GUI program.

---

### Post by sunnypt on 2012-10-18
> **SledgeHammer_999 said:**
> If you want to make a media player you have to choose another programming language. Something like C, C++ or python. You will also want to learn some GUI programming. [Gtk+]("http://www.gtk.org") or [Qt]("http://www.qt-project.org") basically. Both GUI frameworks have bindings for python( and Gtk+ has for C++ too). Also you will need to learn to use [GStreamer]("http://gstreamer.freedesktop.org/") for media playback.
A good tutorial for gstreamer beginners is this->[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html)

But I think this will be too much for you since you are still an amateur and you can't even code a GUI program.
 

oh yeah i know it's still too much for me to handle, i just wanna know where to look about it u know? wanna have resources :) kinda got some ideas that should be fun to do, like a tic tac toe game or something, but i guess for that i need to learn GUI right? what about that Quickly tool? is that nice for that kind of stuff?

---

