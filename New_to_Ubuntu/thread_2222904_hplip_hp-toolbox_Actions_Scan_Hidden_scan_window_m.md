---
title: "hplip hp-toolbox Actions Scan: Hidden scan window menu under Unity"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by jc-junghans on 2014-05-08
Hi alltogether,

I use Ubuntu 14.04 LTS, and I remarked the following annoyance when using the HP Device Manager (hp-toolbox, Version 3.14.3): When I call its Scan window under Unity, I don't know how to access the menu. The main window of the HP Device Manager shows a menu bar (Device View Configure Help), but the "Simple-Scan"-window does not, so I cannot access among others the Scan Settings menu.

To access the Settings menu, I have to call the HP Device Manger under LXDE instead of Unity; then a menu bar is shown. That means if I want to see or to change scanning settings, I have to log out from Unity, to change the Desktop Environment to LXDE, log in again and then call the hp-toolbox.

I tried "unity --reset" from the Terminal, which results in "ERROR: the reset option is now deprecated".

Apart from that, Unity is my favoured Desktop, but is there a way to display the hidden scan menu?

Best regards

---

### Post by linux4me on 2014-05-08
I haven't used the scanning tool from the hplip GUI. I always use Simple Scan, which comes with 14.04 and works great with my HP printer. 

It's not the solution you're seeking, but you might give Simple Scan a try. Just tap the Super key and type "scan" in there. It will find it for you.

---

### Post by jc-junghans on 2014-05-08
Thank you for your fast reply linux4me,

this is strange: When I open the hp-toolbox scan window, it calls what you proposed me to use: simple scan (ps aux => /usr/bin/simple-scan hpaio:/usb/Deskjet...) regardless whether under Unity or LXDE. I didn't know this; I thought the scanning tool belongs to hplip, but it doesn't. But under LXDE, simple scan shows a menu bar (Document Page Help). Under Unity, this menu is not visible. Really strange.

I suppose you see a menu bar in your simple scan-window, and so you can access the Preferences menu? Do you use Unity?

---

### Post by linux4me on 2014-05-08
Yes, I do use Unity in 14.04.

I have to put my cursor over the Simple Scan title bar in order to see the menus because in Settings -> Appearance -> Behavior I have "in the window's title bar" selected in the Show the menus for a window section. The menus only appear when I put the cursor over the title bar. You might check your selection there to see what you have set.

---

### Post by jc-junghans on 2014-05-08
Thank you again linux4me,

at first it didn't work as you described, so I guessed that some piece of software was missing. After some googling I installed the package "indicator-appmenu" which was not present by some reason, and now it works as you described. Thank you!

...

And now, I would like mark this thread as SOLVED, but I don't find any possibility to do that. I cannot find the "Thread tools"-menu  which is being mentioned in another place in this forum. Maybe tomorrow...

---

### Post by linux4me on 2014-05-08
> **jc-junghans said:**
> And now, I would like mark this thread as SOLVED, but I don't find any possibility to do that. I cannot find the "Thread tools"-menu  which is being mentioned in another place in this forum. Maybe tomorrow...

I'm glad you got it working.

For me, the Thread Tools menu is in a gray bar on the right side of the page below the header, breakcrumbs, and thread title. I have Thread Tools, Search Thread, and Display.

---

