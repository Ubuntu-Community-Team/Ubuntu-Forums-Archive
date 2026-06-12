---
title: "Install issue - hangs"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by monkey64 on 2008-11-14
Well this is my first install of a non Windows OS.  I gave up with Vista some time ago...

Firstly I should point out that I'm installing Ubuntu on a Dell Inspiron 2600 Laptop.  Not sure if that's supported, but I can boot into a Live CD using my Backtrack 3 CD.

I have verified the CD and it passed.  I can boot from the CD and get the options of Language Selection etc.  There's lots of whiring from the CD drive and about 10 minutes into the Install, I get some horizontal lines and the machine hangs.

Any ideas.  Sorry I can't be more specific

---

### Post by mapes12 on 2008-11-14
Try the Alternate CD: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

And have a look at the guides from Pyschocats in my sig file.

---

### Post by monkey64 on 2008-11-14
Okay.  The Alternate CD enabled me to install the OS.

However, after installation, I get a kind of bongo drum sound and the screen comes up with 10 horizontal lines and a fairly lightish splash screen.  It hangs and I can go no further.

Any ideas?

---

### Post by mapes12 on 2008-11-15
If you have installed 8.10 then that may be the cause of the lines on your screen. Lots of posts on the Forum about 8.10 and screen/graphic device issues. Give 8.04 LTS a go. Again, alternate CD.

> I get a kind of bongo drum soundThis is normal. Acknowledges that your system has initialised and ready for you to login. A bit like when windoze plays a tune (can't remember what it is anymore) when it starts.

> the screen comes up with 10 horizontal lines and a fairly lightish splash screen. It hangs and I can go no further.This is not normal and may be something to do with the new X configuration in 8.10 - that's my best guess.......

---

### Post by theUg on 2009-03-01
[http://ubuntuforums.org/showthread.php?t=1011213](http://ubuntuforums.org/showthread.php?t=1011213)

That&#8217;s a solution for Xubuntu, it could work with Ubuntu 8.10 as well, but there could be need to remove compiz (search for that one). First try to install it with an external monitor as per write-up, then modify xorg.conf, then see if it works (disconnect external monitor, reboot). If it does not after that, or hangs during load (blank beige screen) &#8212; that&#8217;s a compiz issue, had same thing with other onboard Intel chipset.

P. S. If you already have alternate CD installed, try to go to the recovery mode from start-up, then drop into root prompt, then modify xorg.conf from there, using command line.

---

