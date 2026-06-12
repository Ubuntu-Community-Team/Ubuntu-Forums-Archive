---
title: "Looking for assistance for home media server setup"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by yakinikku on 2013-08-15
Hi guys,

I am looking to build a home media server to take over for my WHS box.  I am going to go with Linux for sure and I have already purchased the parts to perform the install.  Below are the requirements of the box and I am hoping you guys could help point me in the right direction.

•	DAAP
•	DLNA
•	Plex
•	Time Machine Backups
•	Windows Client Backups
•	Storage pooling
•	VPN Server
•	SSH
•	Webmin
•	Transmission

This is my list of things that I need it to do for now.  I have most of them worked out already, but I wouldn’t mind suggestions.  

I have looked at FreeNAS, ZFS on Linux, BTRFS, Amahi and Openmediavault.  Amahi and maybe Openmediavault seem to be sort of the direction I am leaning, but I can’t decide which to go with.  Amahi just released version 7 that is supposed to include a graphical plugin for manipulating the greyhole pool, which is something I would really love to have.  However, I am impatient/excited to get my new server built and don’t know if I can wait much longer for the plugin thing to be released.  I am also contemplating running with Amahi on Ubuntu, even though it's not the latest version.

I think my biggest issue is the pooling.  I have looked in to greyhole and tried configuring it on a VM and I think I got it working, but now I am getting permission denied errors when I try to copy to it as a test.  So if anyone can help me out in that aspect it would be much appreciated.

I wouldn’t mind rolling my own setup using Ubuntu and installing all of the things listed above, but the pooling is where I get stuck.  The unit will have 9TB to start, and that may increase in the near future so it must be scalable.  I do not want a hardware RAID setup for my own reasons, so please no debating about which is better.  

Suggestions appreciated!  TIA guys.

---

### Post by yakinikku on 2013-08-16
Anyone?

---

### Post by Derek Karpinski on 2013-08-16
I'd look into Debian GNU/kFreeBSD [http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

Basically it's Debian with all of the packages it has with the free bsd kernel that supports ZFS natively.

I'm not sure how complete it is or how many bugs it has.  Worth a look though.

Going that route will definitely be a lot of manual setup, but with Debian's massive package list, you should be able to accomplish everything you have on your list.

---

### Post by yakinikku on 2013-08-16
> **Derek Karpinski said:**
> I'd look into Debian GNU/kFreeBSD [http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

Basically it's Debian with all of the packages it has with the free bsd kernel that supports ZFS natively.

I'm not sure how complete it is or how many bugs it has.  Worth a look though.

Going that route will definitely be a lot of manual setup, but with Debian's massive package list, you should be able to accomplish everything you have on your list.

Thanks for the suggestion.  I will have a look.

Does anyone else have any suggestions?  

Is there a reason to choose ZFS over something like greyhole?

---

### Post by CaptainMark on 2013-08-16
Is it a media player/server or server only?

---

### Post by yakinikku on 2013-08-16
> **CaptainMark said:**
> Is it a media player/server or server only?

CaptainMark, it will be a server only, serving up media to media player devices such as a WDTV Live, xbox 360, etc.  It will also be used as a central repository for basically all of my files.  I hope that answers your question.

---

### Post by CaptainMark on 2013-08-16
Then it has to be debian then, its like your Swiss army knife of Linux distros, Debian is anything you need it to be

---

### Post by yakinikku on 2013-08-20
> **CaptainMark said:**
> Then it has to be debian then, its like your Swiss army knife of Linux distros, Debian is anything you need it to be

Not sure what you mean there Mark.  While Debian is certainly ubiquitous, that doesn't mean that apps wouldn't exist for other flavours.  I myself do prefer Debian in most instances because finding pre-packaged .deb files for most things is easy (and I am lazy and don't want to compile things from source), that wouldn't mean that finding that same software would be impossible for other distros.

Ideally what I would like is to have some sort of GUI for greyhole or something similar to greyhole with a GUI.  I don't want to be messing around with things after I get home from a long day at work (in the IT field).  :).  

I also tried OpenMediaVault and I liked it, but the greyhole plugin doesn't work with .4.

From what I have read about LVM there is no way to configure to not take out an entire array should you lose one HDD, is that correct?

---

### Post by yakinikku on 2013-08-21
I think I am still leaning towards greyhole.  I setup a pool (I think?) in a VM and it appeared to be working, but when I try to copy files to it from a different VM I get samba permissions errors.  I don't know what's happening there.

---

