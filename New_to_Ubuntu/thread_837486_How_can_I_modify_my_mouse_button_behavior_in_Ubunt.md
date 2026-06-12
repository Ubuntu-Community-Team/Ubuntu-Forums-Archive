---
title: "How can I modify my mouse button behavior in Ubuntu?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by L a r r y on 2008-06-22
Hi folks,
I would love to get rid of my heavy-handed second finger when it comes to working a mouse.  It rests on the right mouse button, and while I am trying to use the vertical scroll arrows I get sent straight to the end of the document, when this finger decides to lay down on the job.

It wasn't an issue for me in Windows, because I was presented with a context menu -- well, it was an annoyance to have to clear the menu in order to continue what I was doing, but at least the default menu choice under the pointer was usually to scroll down (or scroll up if using the up arrow).

Where can I configure the mouse button action while using the scroll-down and scroll-up arrows?

I am running Ubuntu 8.04 on an AMD Athlon processor, running 1GHz, and a K7S5A mainboard with its on-board video, and a Diamond Multimedia 7.1-surround sound card.

Any help on this mouse issue will help me to stop swearing at the computer every few minutes some days.  :guitar:  Thank you for reading.

---

### Post by uclalinux on 2008-06-22
Hey, I hope I can help, there are 3 ideas that come to mine.

One: System> Preferences> Mouse, here you can change afew things.
Two: Read this it is very helpful [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

Three: this is alot more involved and headaches could occur :), You will need to edit your xorg.conf file located in ```
/etc/X11/
``` you may look at by typing ```
gedit /etc/X11/xorg.conf
```, you will need to find a sections that looks like this
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```
and you may edit it as you see fit. Of course you will need to do alittle background reading before attempting a solution to fit your needs, here is one site I found that will help explane it [http://www.linux.com/feature/118108](http://www.linux.com/feature/118108), just google xorg.conf, and read about it. Sorry I am not more help, but understanding X11, and  xorg.conf is something that is best done with self enlightenment.

---

### Post by L a r r y on 2008-06-22
Thanks, uclalinux, that gives me something to chew on.  I'll let you know how I managed.

---

