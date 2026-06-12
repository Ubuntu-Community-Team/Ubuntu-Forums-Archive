---
title: "Question Concerning The Transfer of a Program from Windows"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by The Real Prometheus on 2012-05-12
In the past I had played around with the dual boot feature and had both Windows and ubuntu operating systems installed.  I recently made a final back up of all my windows files and want to fully jump on board with Ubuntu.  I was wondering if certain programs from Windows which were saved on my external hard drive could be loaded directly to ubuntu.  I believe Itunes cannot be run on ubuntu but I was wondering if simpler programs such as Daemon Tools Lite and DVD burning applications could be?
I'm fairly new to Ubuntu if that could not have already been deduced from my previous statements.
Thanks for the help.
:)

---

### Post by zombifier25 on 2012-05-12
Ubuntu is not Windows. Ubuntu will not run Windows' app (well, they can be run using [Wine](winehq.org), but that's a different story). You need to get out of that misconception first before you can use Ubuntu efficiently. Ubuntu already has excellent native programs (like CD burners in your post. Brasero is installed by default, but K3B is better)

Some cross-flatform apps can have their profile transferred (e.g. Firefox) What programs do you want to save?

---

### Post by The Real Prometheus on 2012-05-12
There was no program that was vital for me in Windows it was simply a compatibility issue that I was curious about.  I suppose although I am not sure that a virtual machine could be set up if I deemed a Windows application an utmost necessity.  Also after doing a little research on the web Ubuntu seems to have alot more diversity in applications then I previously thought.  I guess I can only blame my own ignorance for this misconception](*,)

---

### Post by zombifier25 on 2012-05-12
Don't blame yourself. Stupid people don't exist, only ignorant ones :popcorn:

---

### Post by traditionalist on 2012-05-12
> **The Real Prometheus said:**
> In the past I had played around with the dual boot feature and had both Windows and ubuntu operating systems installed.  I recently made a final back up of all my windows files and want to fully jump on board with Ubuntu.  I was wondering if certain programs from Windows which were saved on my external hard drive could be loaded directly to ubuntu.  I believe Itunes cannot be run on ubuntu but I was wondering if simpler programs such as Daemon Tools Lite and DVD burning applications could be?
I'm fairly new to Ubuntu if that could not have already been deduced from my previous statements.
Thanks for the help.
:)

I have two programs which have to run in windows 7, a banking program and a special printer driver. I installed a Virtual Machine, and then my Windows 7 on that, there are two main contenders;

[https://www.virtualbox.org/wiki/Editions](https://www.virtualbox.org/wiki/Editions)

[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

both work, A matter of choice.

All works great.  For everything else I use native Ubuntu applications.

---

### Post by 3rdalbum on 2012-05-12
> **The Real Prometheus said:**
> I believe Itunes cannot be run on ubuntu but I was wondering if simpler programs such as Daemon Tools Lite and DVD burning applications could be?

It's not so much a case of "simpler programs work", and more a case of "if the programs use the Windows APIs that are best supported on Wine". iTunes is written by people who'd probably rather be programming on the Mac; that should give you an indication of the situation :-)

As for your question about Daemon Tools and DVD burners, it's unlikely they'll work. Daemon Tools adds features to the underlying Windows OS, that is not present on Wine. DVD burners require access to the underlying hardware, which Wine also does not allow.

Linux has some decent DVD burners anyway, and the main feature I've heard of in Daemon Tools is the ability to mount an ISO as if it were a real disk - Ubuntu can do this out-of-the-box.

---

### Post by jaychandran_s on 2012-05-12
Yes, wine is really a **very straightforward** way to run Windows programs, and I have used it to run some of my most **favorite** Windows apps on Ubuntu. But let me remind you, that although the apps **will work quite nicely**, these are **not** made for ubuntu, so never expect them to function as they did on Windows. The best option here is to find an Ubuntu Alternative and learn to live with it!!!

But if you are *very specific,* then YES, wine is **the** solution.

Hope this helps!! ;)

---

### Post by Prescilla on 2012-05-12
You either use Wine.
Or install Virtualbox.

---

### Post by Shadius on 2012-05-12
Also, you can test out the Ubuntu alternatives. I find that some, if not most Ubuntu programs, do a better job than their Windows counterparts. :)

---

### Post by codingman on 2012-05-12
Alternatives for Itunes are like nightingale, rythmbox and some others you might snatch from USC.

There are things like brasero or my favorite; K3B, as a disc burner.

There is, like said in other posts, you can use wine.

---

### Post by jmore9 on 2012-05-12
k3b burns almost anything even blue ray now i hear.  I use k3b for my burning apt.  You can also mount iso's with acetoneiso.  That was a biggie for me.  And most recent versions of linux today can read and write fat32 and NTFS .

Hope this adds a little to knowledge of apps in Ubuntu repo sitting there for the download and install.

---

### Post by flemur13013 on 2012-05-12
"I was wondering if certain programs from Windows which were saved on my external hard drive could be loaded directly to ubuntu."

With any "portable" windows program you can just copy the install directory to the proper place in your .wine directory and run it with wine.  If you unfortunately have to run an installer, run it via wine: $ wine setup.exe

They work best if you do something like this (a 2-line script named ~/bin/audi for me):
```
cd /home/username/.wine/drive_c/Programs/Audition_1.5
wine Audition.exe &
```

The directory "Audition_1.5" was just copied from a windows installation.

Which windows programs will work is iffy.  Because there aren't any good equivalents in linux, I use foobar2000, irfanview and audition, and they all work fine (they're also all "portable").  My DVD maker - ConvertXtoDVD, something with no real counterpart in linux - won't run in wine because of it's own program glitch about a file location, so I still boot windows for that. Fortunately I don't use it very often!

Edit: some "installed" programs will also work with wine if you just copy their directories; try it to find out.

---

