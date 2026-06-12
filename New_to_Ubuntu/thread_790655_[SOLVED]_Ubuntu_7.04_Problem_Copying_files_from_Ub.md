---
title: "[SOLVED] Ubuntu 7.04: Problem Copying files from Ubuntu to Windows XP"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by mixtri on 2008-05-11
Please Help!

I am trying to copy a backup file (52Gb) in size from a folder on my desktop within Ubuntu to a slave hard disk on my computer which boots WinXP.

I messed up the settings in my previous install of Ubuntu 8.04 and unable to access the system. I have since reinstalled ubuntu 7.04 in order to gain access to 8.04's filesystem, so that I am  able to back up my files prior to a clean install of kubuntu KDE4 (I intend formatting the whole disk for this). I tried other methods of backing up but they didn't work for me.

I now have 3 separate installs on my machine. Both 8.04 and 7.04 residing on the same disk but in different partitions i.e sda1 and sda3.

I created a backup image of my 8.04 home folder, but because of its large size  i decided to copy the file across to my winxp disk which has ample space. I don't have an external disk for this task.

I cannot copy the file to windows using root permissions as it says the disk is read-only.
It won't let me change the owner of the disk in /media either.

Any suggestion peeps? 

I'm thinking maybe i should create a new partition on my current disk with just enough space to hold the file and format the rest of the disk for my fresh install of kubuntu that way i eventually might be able to import my backup file into kubuntu. Is there an easier way to the desired goal.

---

### Post by annda on 2008-05-11
writing to ntfs disk (the windows filesystem) is possible wthout installing any tools on hardy. feisty needs a special driver called ntfs-3g.

this [guide]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") has a lot of screenshots to illustrate the installation and configuration.

good luck!

PS. if you have enough disk space, creating a separate partition for backups is a good idea.

---

### Post by mixtri on 2008-05-11
Thanks for the link and avice. I will try it out and let you know how i got on. fingers crossed.
:)

---

### Post by mixtri on 2008-05-12
Hey Aanda!
Thanks for the tip. the driver was just the ticket. several hours gone since posting this thread and I am now enjoying my new found system.
All problems solved at the moment.
:popcorn:

---

