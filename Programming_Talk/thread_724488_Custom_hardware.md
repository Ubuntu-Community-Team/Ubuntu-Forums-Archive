---
title: "Custom hardware"
date: 2008-03-14
forum: Programming Talk
---

### Post by madsporkmurderer on 2008-03-14
I am thinking of making some very simple custom hardware, but want to find out what will be needed software-wise before I start a project that could run into difficulties. Essentially what I want is a set of front panel buttons that can control Amarok on a media box, what I was thinking was to have the system recognise them as some sort of keyboard key or something then just use amarok global shortcuts.

I have been told the parallel port is nice and easy to interface with, but have never seen a paralleled port keyboard, would I be better off using another port? Also is there likely to be some sort of conflict because there will also be a standard keyboard attached?

Assuming I have got this far without major stumbling blocks, I'm thinking that I would be writing my own driver, anyone got any information regarding what is involved in this?

Thanks in anticipation,
Mike

---

### Post by Zeotronic on 2008-03-14
> what I was thinking was to have the system recognise them as some sort of keyboard key or something then just use amarok global shortcuts.
Forgive me, I don't know anything about hardware in the capacity your talking about it, or amarok, but why would you want them to be recognized as keyboard keys rather than joystick buttons?

---

### Post by Fbot1 on 2008-03-14
Writing drivers is a pretty involved process.

---

### Post by madsporkmurderer on 2008-03-15
> **Zeotronic said:**
> Forgive me, I don't know anything about hardware in the capacity your talking about it, or amarok, but why would you want them to be recognized as keyboard keys rather than joystick buttons?

Amarok has a feature called 'global shortcuts' whereby you can tie particular keys/key combinations to functions (F3 could be tied to play/pause, or Alt+Z to skip backward for example) these shortcuts work even when Amarok isn't the active window. I hadn't considered joystick buttons, and don't know if global shortcuts can be tied to them but that does sound like a god idea- are joysticks standard hardware?

---

### Post by madsporkmurderer on 2008-10-05
I finally got round to doing this. I realised that in order to get them recognised as keyboard buttons I might as well just install the buttons so that the mad ethe same connections in the keyboard as the keys they are emulating. This way al th debouncing/encoding is taken caare of by the keyboard controller.

The keyboard still functions normally, but now  has an extra wire ocming out the back with a set of buttons on the end- they emulate F2-4 and F6-8. I have assigned these to amarok global shortcuts.

---

### Post by wd5gnr on 2008-10-05
If you have a serial port (or a USB serial port) look at [http://www.awce.com/gp3.htm](http://www.awce.com/gp3.htm). Source code libraries compile under Linux and parallel ports are vanishing on PCs these days (note you can't use most if not all USB parallel ports for I/O -- they "hook" right into the printing system).

---

### Post by Zugzwang on 2008-10-05
In the good old days, there have been this standard 15-pin joystick connectors. It is very easy to build some custom hardware interfacing with them (if 4 keys suffice - With some tricks you can add another e.g. 8 buttons by converting the axes to buttons). 

In that case you don't even need drivers, building some daemon reading the joystick's position from time to time and injecting key-strokes to the X-Server suffices in that case.

There are some boxes you can buy for interfacing an old joystick with a modern USB port, maybe there exist Linux drivers for them.

As already pointed out, writing drivers is not quite easy, but this way wouldn't require that.

Making parallel port devices is a little bit more complicated as modern parallel ports do not support the old plain access protocols anymore. Look at the huge number of different cables for interfacing an old C64 disk drive - the cables for the old parallel ports are simple whereas the other's aren't.

---

