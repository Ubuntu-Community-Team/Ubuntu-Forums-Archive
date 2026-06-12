---
title: "HOW TO: Install Lexmark Z1270 all in one in VMWare in Edgy"
date: 2006-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by BLTicklemonster on 2006-12-29
Okay, I installed my new Z1270 with the Z600 linux drivers, but it only printed, it won't scan. I have XP in VMWare, so I decided to try that.

When you boot to XP, have the scanner on, and the install cd in the tray, and regardless of the warnings from Lexmark to the contrary, let windows install whatever drivers it wants to install. If it says it can't find any, manually install using the windows install wizard from the cd, using the inf file found in the drivers/eng folder.

What happened to me was, it only installed printer drivers. Duh. What did I expect? Have no fear!

At this point, navigate to your cd folder, and install the software from there. If it says you don't have a printer, then go to the VMWare toolbar, and click on V_M_ and go to removable devices/usb and click on your printer and run the install software again. 

Sure, it stinks, but what the heck, I can scan now without actually leaving Linux, per se.

---

### Post by blackhole82 on 2007-02-06
I wonder if this would help to install the drivers for my lexmark x2470.  It is a shared printer on my windows box.  My goal is to print to it soley from Ubuntu.  Would it be possible to install the driver(s) then move them to cups using VMWare?  I've never used that before.

---

