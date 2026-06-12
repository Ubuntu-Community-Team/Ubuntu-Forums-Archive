---
title: "Monitor recommendations?"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by favila1998 on 2012-02-20
I think I'm having the monitor refresh problem that others have encountered w/ Acer monitors. After the BIOS screen flashes, I get "input not supported" and then a bunch of actions items with a list of whether it was "ok" or "failed". I always have "System V runlevel compatibility" as a "fail". 
 
I'm a complete novice and don't even know how to find a command prompt to monkey around with settings. **My question: **Since I was planning on buying a new monitor anyhow, any recommendations as to monitors that I could use with which Ubuntu would be immediately compatible so I don't have to do any of that? Thanks in advance for any leads!
 
(I installed Ubuntu 11.10 onto the hard drive of a computer that I had (for which Windows 7 just completely stopped working) by using a USB drive. Ubuntu runs great off of the USB drive (as well as off of a DVD installation disk I also made), but I can't get it to run off of the hard disk installation b/c of the monitor compatibility problem.)

---

### Post by larrypg on 2012-02-20
Hello,

That sounds more like a video card driver problem than a monitor problem.  I have never had to do anything with a monitor other than plug it in.

---

### Post by favila1998 on 2012-02-20
The forum threads that I have read on this seem to indicate that it is a monitor problem in that the default settings don't jibe with Acer's monitors. 

Since I've posted my first question, I've figured out how to get to the terminal and also how to edit xorg.conf and I think I have the correct specifications to get the monitor to work.  Of course, I can only do this by booting using the DVD, and trying to edit xorg.conf on the hard drive, the computer won't let me save b/c it says I'm not the owner.  Any ideas on how to address that?

One way or another, I'm going to get this thing to work!

---

### Post by cortman on 2012-02-20
I'm not knowledgeable enough to tell you how to fix your xorg.conf, but I can give you a recommendation on a monitor: I just bought a Benq EW2420. It's a VA (vertical alignment) panel, and the color reproduction and viewing angles blow all my TN panels out of the water. It's very inexpensive as well (I paid $220 for it, 24"). So far it's worked perfectly on HDMI with my Ubuntu 11.10, and I would recommend it to anyone in search of a good, inexpensive monitor.

---

### Post by 1clue on 2012-02-20
Are you using a CRT (old-fashioned monitor that's approximately as deep as it is wide) or are you using an LED/LCD/similar flat panel that's only a couple inches thick?

If you're using a CRT then you can most certainly choose a resolution that's not supported.  Also if you're using a flat panel and the old style cable with the not-quite-rectangular connection then you can also possibly find a combination that the monitor can't support.

Personally I would recommend a digital video card that has the new DVI-style port rather than the old connector, and a LCD or LED monitor.  They're pretty cheap now.

I use LG or ViewSonic right now, but almost any modern monitor will work.  That's not true with video cards unfortunately.

---

