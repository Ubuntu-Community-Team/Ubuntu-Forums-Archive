---
title: "Problems Installing Ubuntu"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by russella on 2008-11-22
Hi All,

I am a complete Linux Noob but was really impressed when a friend showed me the latest version of Ubuntu yesterday.  When I go home I quickly downloaded the latest copy, Checked the MD5 hash and burnt the ISO to a CD using the recommended software.

I started the install on a test Dell optiplex GX240 machine I have all seemed good,it got past 50% copying files and then stopped with the followin error;

the installer encountered an errorcopying files to the hard disk [errno 5] Input/Output error.

First I burnt another disk and tried again, same problem seemed to get a little further on but where it gets caught out seems to be random.  Tried changing the CD-ROM drive three times same issue.  The software will boot from the disk fine and the software loads up ok as soon as you click ok to the error but it seems it's only booting from the CD-ROM and mothing is writing to the disk.



Tried another hard disk and the exact same error.  Please can someone help am I missing someting fundamental!! 7 hours later still no working system and I'm losing the will to live. Really want to play with this awsome looking O/S.

Reagrds 
Russ

---

### Post by shifty_powers on 2008-11-22
get the alternste installer disk.

you'll find a link to it on the get ubuntu front page. (it's a text link)

it's a text based installer rather than using a gui and is not a livecd. it si intended, amongst other things, as a failsafe.

also, when you boot, have you tried the check cd for defects option before you go into the desktop?

---

### Post by phantomjoker on 2008-11-22
have you tried downloading the file again - you might have (some how) downloaded a faulty copy, or a part has been missed from your download - if you keep getting the same error, but are changing the disks, hdd's etc - it's most likely the download is the problem.

I assume you got it from the ubuntu website - but here's a link to a file i used, and works...

[http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/intrepid/ubuntu-8.10-desktop-i386.iso]("http://mirror.ox.ac.uk/sites/releases.ubuntu.com/releases/intrepid/ubuntu-8.10-desktop-i386.iso")

---

### Post by RedRat on 2008-11-22
It sounds like you might have some problems on the hard disk. Are you installing it to a clean disk? How did you prepare the partition? Do you have enough room on the partition?

---

### Post by russella on 2008-11-22
The CD check is showing no errors.  I am setting the partition to use the entire disk.

There seem to be no errors when partitioning only when copying the files from the cd-rom to the disk.

Russ

---

### Post by RedRat on 2008-11-22
> **russella said:**
> The CD check is showing no errors.  I am setting the partition to use the entire disk.

There seem to be no errors when partitioning only when copying the files from the cd-rom to the disk.

Russ

How old is your computer and that particular CD/DVD unit? It does happen that CD units do crap out on occasion, I have one that is about 4 years old and it is a bit flaky.

---

### Post by russella on 2008-11-22
They are all pretty old but thought one of them may have worked.  Just in case they are dead I have copied the data to a USB stick following a posted guide. This is fine but rather than copying the files to my hard disk it's just booting directly from the USB stick directly into Ubuntu.

Russ

---

### Post by RedRat on 2008-11-22
> **russella said:**
> They are all pretty old but thought one of them may have worked.  Just in case they are dead I have copied the data to a USB stick following a posted guide. This is fine but rather than copying the files to my hard disk it's just booting directly from the USB stick directly into Ubuntu.

Russ

When it boots into Ubuntu directly is there a desktop icon that says something like "Install Ubuntu" or similar?? Been a long time since I installed from the CD or other source. When it does boot from the USB, do you have internet connectivity? For example, can you open Firefox and go out on the internet?

---

### Post by russella on 2008-11-22
Ok,

There is an install icon when you boot in from the USB drive, sorry must have been blind not to notice that.  Tried installing again but from the USB drive this time and again the same error.  Put a third 40GB drive in of a different make and tried again and the message again.  Convinced this is now nothing to do with;

- CD Drives   (Tried 3)
- Hard Drives   (Tried 3)
- USB Drive    (Tried 1)

In the process of downloading the ISO again to see if that may have been bad (Checksum was showing correctly)

Running out of ideas here!!  But thanks for everones amazingly quick support.

Russ

---

### Post by RedRat on 2008-11-22
> **russella said:**
> Ok,

There is an install icon when you boot in from the USB drive, sorry must have been blind not to notice that.  Tried installing again but from the USB drive this time and again the same error.  Put a third 40GB drive in of a different make and tried again and the message again.  Convinced this is now nothing to do with;

- CD Drives   (Tried 3)
- Hard Drives   (Tried 3)
- USB Drive    (Tried 1)

In the process of downloading the ISO again to see if that may have been bad (Checksum was showing correctly)

Running out of ideas here!!  But thanks for everones amazingly quick support.

Russ

Must agree with you. It does look like you have a faulty download. Try again, but if it happens again you might want to just get the CD/DVD from ubuntu. the cost is nominal.

---

### Post by shifty_powers on 2008-11-22
have you tried the alternate install cd that i suggested?

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by jyaan on 2008-11-22
Just a warning -- It might be your motherboard. I had a similar problem where no hard drives would work. They would run a little while, but then come up with that error and all disk activity would fail. I ended up running a live CD distro with USB drives for storage until I bought this new one. I hope that's not the case for you, though.

---

### Post by russella on 2008-11-22
Just downloaded the ISO again, re-created my USB boot disk loaded into Ubuntu and installed from the menu.  Again same problem this time got to 56% copying files.

Maybe I am doing something fundamental wrong with the partitioning or do I need to prep the harddisk or something?

Am leaving guided partitioning on but there are some advanced options should I be in there?  Have notive sometimes partitioning is different e.g sometimes 2 partitions sometimes 3.

LOL, already ordered the disks just being impatient as normal.

---

### Post by heroidi on 2008-11-22
> **russella said:**
> Just downloaded the ISO again, re-created my USB boot disk loaded into Ubuntu and installed from the menu.  Again same problem this time got to 56% copying files.

Maybe I am doing something fundamental wrong with the partitioning or do I need to prep the harddisk or something?

Am leaving guided partitioning on but there are some advanced options should I be in there?  Have notive sometimes partitioning is different e.g sometimes 2 partitions sometimes 3.

LOL, already ordered the disks just being impatient as normal.

the disks you orderd will take a time until they come i have orderd one 6 weeks ago but they are not here :S:S yet

---

### Post by chazn85 on 2008-11-22
just a thought but has a format with a gparted live cd been tried?  by that i mean formatting your disks as you would in the install process

---

### Post by russella on 2008-11-23
Just to let everyone know the problem is related to the motherboard.  Having tried the disk on my wifes laptop it worked first time no issues at all.  Not a single driver issue in sight!!

Just got to persuade the missus to stick with Umbutu now as a replacement for XP.  So far so good.

Thanks for everyones help.

Russ

---

