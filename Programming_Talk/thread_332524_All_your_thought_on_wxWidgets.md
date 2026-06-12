---
title: "All your thought on wxWidgets"
date: 2007-01-06
forum: Programming Talk
---

### Post by theDentist on 2007-01-06
Hi all,

I'm starting to program using wxWidgets for cross-platform apps, What's everyone's opinion on this sytem, and are there any problems in transporting to other platforms.   :-k

---

### Post by gh0st on 2007-01-06
I'm looking at wxWidgets for cross-platform apps as well so I'd be interested to know what people think as well.

Good question by the way :D

---

### Post by theDentist on 2007-01-06
Are you having any problems? I am using dialogblocks on both Windows and Ubuntu, Any problems getting it to work on Windows.  I had few problems on Ubuntu, but on Windows I spent hours to get it to work!  :mad:

---

### Post by Ansible on 2007-01-06
I use dialogblocks to create/maintain the C++ files on windows, but I don't use it for compiling, so can't help you there.  Anyway, the C file create stuff works fine for me, I keep dialogblocks and visual studio open at the same time, and switch back and forth.

So, I've been using wxWidgets for a while now on windows, to me its an improvement on borland C Builder, but there have been a few bugs along the way, specifically in joystick support and theres a wierd bug with the interprocess communication that I'm trying to work out, when the interprocess communique happens before the app starts all the way.  

Another misgiving I've had is that I heard the VLC project is abandoning wx for QT.  I don't know what all the issues they've had with wx are, but I think some of them are related to unicode and internationalization.  I didn't find a whole lot of info from searching the VLC dev forums though.  

But despite the negatives, on the whole I like wx, it seems to be fairly well laid out with many useful classes.  Just as long as you are on board with its philosophy you are ok - ie emphasis on native widgets and not on custom skin type things.  Although there is some development in this "custom look" area in the wx world, it seems to be on the margins and not in the mainstream wx branch.

---

### Post by Ansible on 2007-01-06
Oh yeah, and I recently installed and built wx on ubuntu, and it was about 100x easier than windows.

---

### Post by theDentist on 2007-01-06
I found the problem with windows is I couldn't find out how to use the linux commands in windows, which you seem to have to do to compile the wxWidgets installation in Windows,  We are all used to the command line in Ubuntu but does anyone know how to compile the wxWidgets in Windows using the command line?  In the end I had to compile wxWidgets with dialogblocks, which happens to have a menu item that does it, but I failed to get the GCC compiler to work that way, only the VC++ one.

---

