---
title: "Disk drives are not accessible!"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Ghalebi on 2013-01-10
Hello

I am a real absolute beginner .. I just installed Ubuntu 12.10 instead of Windows 7 .. the first thing shocked me is that I am not able to access disk partitions (C:/ D:/ ... etc) 

Any help!

---

### Post by Bashing-om on 2013-01-10
Ghalebi; Hi ! Welcome to the forum.

Question; When you installed ubuntu, did you install such that ubuntu is the sole operating system on your machine ?

Tutorial: disk devices. Ubuntu (linux) has a different convention/nomenclature for them.
The first Serial Device ->sda (a=1st drive), now comes the partitions sda1 -> 1st drive,1st partition//sda2 = first hard drive second partition// sdb4 = second hard drive 4th partition.

In order to see the partitions external to ubuntu, these partitions must be mounted to the ubuntu file system.
Nautilus - ubuntu's file manager - does this automatically. The left pane in the file manager list all file systems that ubuntu is aware of. At this time they (file systems) may have a strange name as in "194 GB Filesyst.." When you click on the file name the device will be mounted and accessable. Later you can give a more meaningful "label" to the device (file system)[all things in linux are files].

Depending on what you have and what you want to do, other options exist to mount partitions.
[INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by Ghalebi on 2013-01-13
Dear [B]Bashing-om
[/B]
Thanks for your reply! I've installed Ubuntu as a solo system!

I've installed gparted .. attached is a snapshot .. I can't find partitions which I had on Windows 7 .. have they been formatted :frown:

Many thanks!

---

### Post by 3rdalbum on 2013-01-13
> **Ghalebi said:**
> Dear [B]Bashing-om
[/B]
Thanks for your reply! I've installed Ubuntu as a solo system!

I've installed gparted .. attached is a snapshot .. I can't find partitions which I had on Windows 7 .. have they been formatted :frown:

Many thanks!

Unless you have more than one hard disk, it looks like you only have the Ubuntu partition.

Your words "I've installed Ubuntu as a solo system" indicate to me that you probably clicked the option to "Erase hard disk and install Ubuntu" - which would certainly erase the whole hard disk.

---

### Post by Mark Phelps on 2013-01-13
Why the frown emoticon?  

You said > I just installed Ubuntu 12.10 instead of Windows 7

So, you got what you asked for!

---

### Post by Ghalebi on 2013-01-14
> **Mark Phelps said:**
> Why the frown emoticon?  

You said 

So, you got what you asked for!

Windows 7 was installed on C:/ drive, not on the whole disk!

---

### Post by JRV on 2013-01-14
Ubuntu is installed on the whole disk.
You may not realize it but that is what you told it to do.
Windows 7 is **gone**.

---

### Post by Ghalebi on 2013-01-14
Fair enough guys,, here we go linux!

---

### Post by Bashing-om on 2013-01-14
Ghalebi;

Welcome to a great operating system; And even greater support.

[INDENT][INDENT]enjoy ubuntu <== BDQ

[/INDENT][/INDENT]

---

### Post by Ghalebi on 2013-01-15
Thanks ***Bashing-om*** !

But what does BDQ mean!??
> hth <== BDQ
enjoy ubuntu <== BDQ

Best!

---

### Post by Bashing-om on 2013-01-15
Ghalebi; Hey

BDQ ..just my real initials as opposed to my moniker //if it is confusing will discontinue the practice. ie: it is not Best Done Quickly :

[INDENT]response invited.
[/INDENT]

---

### Post by iMac71 on 2013-01-15
> **Ghalebi said:**
> Fair enough guys,, here we go linux!on your computer, C: and D: are (or better: they were) logical drives, not physical.
Therefore, when, during the installation process,  you've chosen to format the entire disk, you've formatted the physical disk... and Windows 7 has gone and even the two logical drives have been lost.
But don't worry too much: you're still able to run Windows applications, if you wish, simply by installing Virtualbox and then by creating a virtual Windows 7 machine, if you have a medium for installing that OS.

---

