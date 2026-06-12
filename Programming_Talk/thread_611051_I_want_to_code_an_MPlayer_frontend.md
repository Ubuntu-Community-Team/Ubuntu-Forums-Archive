---
title: "I want to code an MPlayer frontend"
date: 2007-11-12
forum: Programming Talk
---

### Post by amgeex on 2007-11-12
Hello all programming people around here, nice to meet ya. Well, to the point: I want to code (build from scratch) an MPlayer frontend. Why? Because all available frontends at the moment are either damn ugly, not user friendly, or don't offer enough control (like Gnome MPlayer). So I decided I want to code a nice and simple, but good looking and user friendly frontend for MPlayer.

The thing is, I don't have a clue were to start, and I would like to hear some opinions from you guys before trying my hand at this. I'd like to know what I'd have to read and learn beforehand to be able to program this thing. The one thing I know is that I want to use the clutter toolkit to draw the GUI, so it looks nice and uses GTK2, etc.

I have (some) experience coding in Java and C++, but I'm not by any means a code guru, so that's why I'm asking for help here.

Thanks a lot in advance!

---

### Post by amgeex on 2007-11-12
I can't believe no one knows about this here... Are there C++ bindings or "hooks" for mplayer? I know there are C and Python bindings for xinelib, but I've never seen that kind of stuff for mplayer... Anyone cares to give me some advice?

---

### Post by cyberjockey on 2008-02-03
u can see mplayer slave mode. also if u want to make it a gnome mplayer frontend then try looking at gstreamer. if u want more inputs i can give all the help i have little somewhat working code somewhere .. but i dont have time to finish it. 

cyber

---

### Post by amgeex on 2008-02-03
Hey man, I had already forgotten about this thread, but I'm still interested in the project. I was thinking about using wxWidgets or something like that to make the frontend multiplatform, you know, so its not limited to GTK2 or Qt, but I'm still not sure. 

I was looking at the slave mode of MPlayer, and I guess that's the way most frontends work? Anyway, I'll look a bit more into it, and if you could show me that code of yours it'd be great to get some ideas. Thanks for replying man! =D

AMGeeX

---

### Post by andrew.46 on 2008-02-04
Hi,

 Have you had a look at the source for smplayer?

         Andrew

---

### Post by rvm4000 on 2008-02-04
> **amgeex said:**
> Hello all programming people around here, nice to meet ya. Well, to the point: I want to code (build from scratch) an MPlayer frontend. Why? Because all available frontends at the moment are either damn ugly, not user friendly, or don't offer enough control

:(

AFAIK there's no library to control mplayer. You need to call mplayer, read and process its output, and send commands using the [slave mode](http://www.mplayerhq.hu/DOCS/tech/slave.txt).

You can embedded the video in your application by using the -wid option.

---

### Post by RawMustard on 2008-02-05
[http://gentoo-wiki.com/HOWTO_MPlayer#Using_mplayer_in_slave_mode](http://gentoo-wiki.com/HOWTO_MPlayer#Using_mplayer_in_slave_mode)

Setting up a named pipe(fifo)works great!  You can control it with a simple webpage pointing your links to a python or bash script that translates your commands into mplayer recognisable ones :)  The same can be done from fluxbox menu so you don't need a gui :)

---

### Post by amgeex on 2008-02-05
Thanks for the replies people, I'm looking at the slave mode of mplayer, and also snooping around the smplayer source code, and when I have a little time I'll try my hand at it and see what happens, I'll let you guys know what's up. 

AMGeeX

---

### Post by bince on 2010-07-25
an mplayer pygtk gui tutorial [http://mymplayer.blogspot.com/2010/07/mplayer-front-end-gui-code.html](http://mymplayer.blogspot.com/2010/07/mplayer-front-end-gui-code.html)

---

