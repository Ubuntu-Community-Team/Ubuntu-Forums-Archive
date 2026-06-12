---
title: "a USB control"
date: 2010-01-07
forum: Programming Talk
---

### Post by cazz on 2010-01-07
Hi I guess this is not so easy but I was thinking about ask here and try in Linux before I give up and run windows.

Is is possible to easy create a one or two button control that use USB.

I want to control a script in the terminal (start and stop the script) and use control to that.

It is maybe a little easy in windows but I like to give Linux a try because it is free and I like to use it for my experiment.

---

### Post by Zugzwang on 2010-01-07
So first of all you will need to make a USB device you can plug into your computer. As this is a non-trivial task, may I propose the following: Go and buy a joystick for little money and paint the buttons red and green (or something like that). You can also remove the circuit from the joystick and put it into a different case or something like that. This saves you the hassle of building a USB circuit and writing drivers. It's also highly likely to be cheaper.

Then you can program a small deamon program that watches for button presses on the connected joystick and reacts according to that. That task shouldn't be harder than in Windows.

---

### Post by cazz on 2010-01-07
Thanks, it was a good idea about the joystick/Gamepad.

But the last one, is that any good guide or something to read?

---

### Post by Zugzwang on 2010-01-07
Daemon writing: [http://www.netzmafia.de/skripten/unix/linux-daemon-howto.html](http://www.netzmafia.de/skripten/unix/linux-daemon-howto.html)

As for the joystick is concerned, there are some libraries for accepting it. Use google to find one.

BTW: There's already a joystick daemon project around: [http://sourceforge.net/projects/joyd/](http://sourceforge.net/projects/joyd/)

---

