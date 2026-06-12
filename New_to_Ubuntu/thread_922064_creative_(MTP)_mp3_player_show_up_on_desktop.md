---
title: "creative (MTP) mp3 player show up on desktop?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by clstal on 2008-09-16
I have a creative vision M mp3 player.  It's recognized and working in Gnomad2 and Rhythmbox.  

I'd like to be able to treat it like I treat my USB drive and have it show up on the desktop when I connect it (via USB).  (I don't want to use gnomad or rhythembox to interact with it).  

Is this possible?  If so, how?  This isn't something I've seen answered elsewhere, though I've seen it asked.  

Thanks!
Crystal

---

### Post by kostkon on 2008-09-16
> **clstal said:**
> I have a creative vision M mp3 player.  It's recognized and working in Gnomad2 and Rhythmbox.  

I'd like to be able to treat it like I treat my USB drive and have it show up on the desktop when I connect it (via USB).  (I don't want to use gnomad or rhythembox to interact with it).  

Is this possible?  If so, how?  This isn't something I've seen answered elsewhere, though I've seen it asked.  

Thanks!
Crystal
Yes, it is, if you are using 8.04. You'll have to install the [*mtpfs*]("http://packages.ubuntu.com/hardy/mtpfs") package (using *Synaptic*, of course).

---

### Post by clstal on 2008-09-18
> **kostkon said:**
> Yes, it is, if you are using 8.04. You'll have to install the [*mtpfs*]("http://packages.ubuntu.com/hardy/mtpfs") package (using *Synaptic*, of course).

Kostkon,

Installed mtpfs noprob... now what?  Is this something I have to run or should an icon appear on my desktop when I plug my mp3 player in?  (Because this hasn't happened, though the mtpfs install wasn't a problem.)

Thanks!
Crystal

---

### Post by Nepherte on 2008-09-18
There's a way to show all mounted devices (your linux disk/partition excluded). It should also show your usb mp3 player. I'm not sure if that's what you're after.

Open up gconf-editor
[code]gconf-editor]
and navigate to apps > nautilus > desktop. Enable 'volumes_visible'.

---

