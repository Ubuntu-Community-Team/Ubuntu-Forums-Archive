---
title: "[TKINTER] Print text into a frame / Open new window"
date: 2011-07-24
forum: Programming Talk
---

### Post by GTMoraes on 2011-07-24
Hey, I'm starting with Python/Tkinter and I need some help here..

So, I'm doing a Cinema Management program, which is responsable for reserving seats, counting money.. that sort of thing.

I've managed it to work as I desired on a command line interface, but now I want to go further and get a GUI for it.

So far, I made it show buttons for each seat, colour it green when free, pink when customer bought with half-price, and red when it was bought full-priced, radio buttons for Full and Half price and placed the buttons for Undo reservation (still not working, I'm thinking about keeping it pressed while User's removing reserves, and when user clicks it again, it de-presses), show the current income (which I want it to be printed on a white frame I made) and a quit button (I would like it to pop a new window with an "are you sure?" question)

Currently, when I click to reserve a seat, it prints "Seat reserved - Full/Half price" on the IDLE window. There's a white frame I placed for using like a "console", but I don't know how to make it print there.
If possible, I'd also like to make it scrollable
[s]Also, I'd like to, when user press the "Quit" button, it pop up a new window asking if user is sure about quitting.[/s]

How should I do it? I've googled a little, but I didn't find any good answer

Thanks
-------------
I found a way to create a dialog window. I needed to use the "Toplevel" command.
I'm currently working on the Quit button
---------------
Alright, I made the quit dialog, but I don't know how to write "Are you sure you wish to quit?" on the dialog.
There's just two buttons sitting there. I tried using "Label", but no luck

[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Big Rig PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by GTMoraes on 2011-07-24
Alright, progress report.

I've found out a way to put text on frames. They work beautifully.
Also I managed to make a working Quit dialog. Amazing!

But now I need to make a look-a-like Console, with scrollable text and all.

Like, when I click on Seat 01, it prints down there "Seat reserved", and when I click on Seat 02, it prints "Seat reserved", but jumping a line and keeping the first "Seat Reserved" there.

This is actually happening, but on IDLE. 

How do I put it on a frame?
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Big Rig PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

