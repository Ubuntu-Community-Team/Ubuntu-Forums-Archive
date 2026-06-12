---
title: "How do I give network access to my external hard drive? [PIC!]"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by alecwh on 2008-11-03
Hello,

I've asked this before, but I didn't get a response, probably because it seemed complicated in writing. So, I've included a picture (from Inkscape) visually describing my question.

What I want to do is gain access (from my laptop) to my desktop's external hard drive, which is /media/ALECBACKUP/. Here is the picture:

[IMG]http://img217.imageshack.us/img217/2672/networkum7.png[/IMG]

I'm a networking noob, so I really have absolutely no idea how this is done. Can someone describe how I can do this (preferably step-by-step, I mess things up easily)?

Much appreciated in advance - I can't wait to watch movies on my laptop (without connecting my external HD manually).

**Edit: I'm on Ubuntu 8.10.**

---

### Post by fornix on 2008-11-03
Is your desktop running XP or linux?

---

### Post by Pro-reason on 2008-11-03
It depends on what sort of networking you want to use.  I personally use SSH for this sort of thing.  I just set it up, and then type &#8220;ssh -X shared@laptop&#8221; into a terminal.  I can then use that terminal to do anything with any file on the laptop.  Or vice-versa.

---

### Post by crispy_420 on 2008-11-03
Based on your drawing and the wording of the descriptions, you are using some form of linux on the desktop. So my suggestion is either samba or NFS, then maybe map the drive on your laptop. Also maybe a static IP for your desktop as well.

---

### Post by fornix on 2008-11-03
I recommend using NFS if the host is a linux machine or samba if its windows.

using NFS lets you feel the hard disk is plugged in your own machine!

More info about NFS can be found here.
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

