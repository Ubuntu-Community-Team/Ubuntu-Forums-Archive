---
title: "backup data files"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-08
I am in the process of switching from windows to ubuntu. I use a laptop and a desktop.Both are duel boot systems.
I have separate partitions on both called "data" which i have left as ntfs so i can still access from windows.

When i am at work i want to be able to backup from the data partition to a usb stick how can i do this in ubuntu? 

In windows I used a program called synchromagic is there a simple way to do this in ubuntu?

---

### Post by keplerspeed on 2008-11-08
Conduit seems like all the rage:

[http://www.ubuntugeek.com/conduit-synchronize-your-data-in-easy-way.html](http://www.ubuntugeek.com/conduit-synchronize-your-data-in-easy-way.html)

I do believe it can backup and synchronise directories.

---

### Post by FrostyFlames on 2008-11-08
You could tar the whole drive or copy with cp.

---

### Post by keplerspeed on 2008-11-08
Copying is ok... but sometimes synchronisation is much more convenient, and faster if there is a large amount of data.

---

### Post by stinger30au on 2008-11-08
[SIZE=2]piece of cake

inside windows run this program

[/SIZE]   [SIZE=3][B][SIZE=2]SyncBack Freeware V3.2.19.0
[http://www.2brightsparks.com/downloads.html#freeware](http://www.2brightsparks.com/downloads.html#freeware)


run it inside ubuntu using wine
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
[/SIZE]     
[/B][/SIZE]

---

### Post by corkscrew on 2008-11-08
Have you tried running it under wine? I tried synchromagic and i was getting some funny results so i dont trust it

---

### Post by mdpalow on 2008-11-08
See QuickStart link in my signature below.

Good luck

---

### Post by kansasnoob on 2008-11-08
> **mdpalow said:**
> See QuickStart link in my signature below.

Good luck

That looks awesome!

I'll be giving it a whirl soon!

---

### Post by corkscrew on 2008-11-09
This looks like the very thing to all the backup stuff when you have a dual boot system. I'm definatley going to give it a go

---

### Post by TVC15 on 2009-03-21
Hi there,

Backup utilities seem to be a hot item on the forum.  A lot of people want something that looks and feels similar to the popular Windows tool Syncback.

For Linux, the best backup tool for me (and surely many others) is rsync.
Best of all: rsync now has a GUI called grsync that you can find in the Ubuntu repositories.
Looks and feels a lot like Syncback and also works on Samba shares or mounted network drives or over an ssh, ....

Very much worth giving a try!


Good luck!

---

