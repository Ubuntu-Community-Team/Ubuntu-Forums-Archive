---
title: "Problem after installing"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by Leevi_Hiekkinen on 2015-01-22
After I install ubuntu on my computer, it reboots and then it goes back to the ubuntu booting screen where it says "Try ubuntu", "Install ubuntu" and some other stuff. I tried installing ubuntu again by clicking the "install ubuntu" but the same thing keeps happening.. Does anyone else ever had this problem? Because I think it's kinda weird. Also, when I'm in the progress of installing ubuntu, if I leave it alone and go make a sandwich or something, it reboots while it's installing ubuntu.. Weird right? Help please.

---

### Post by Bashing-om on 2015-01-22
Leevi_Hiekkinen; Hi ! Welcome to the forum .

My initial thought is in respect to legacy partitioning's limit of 4 partitions to the hard drive.
Show us what we are working with, and what is:
Fire up the liveDVD(USB) to "try ubuntu"
At the desk top activate a terminal with  key combo ctl+alt+t.
Post back the outputs of terminal commands - Between Code tags, please :
```

sudo fdisk -lu
parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
so we know the type of partitioning and how the hard disk(s) are laid out, and what operating systems are installed where.
Once these are known we can give direction on what it will take to boot ubuntu.

Hopefully
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Leevi_Hiekkinen on 2015-01-22
> **Bashing-om said:**
> Leevi_Hiekkinen; Hi ! Welcome to the forum .

My initial thought is in respect to legacy partitioning's limit of 4 partitions to the hard drive.
Show us what we are working with, and what is:
Fire up the liveDVD(USB) to "try ubuntu"
At the desk top activate a terminal with  key combo ctl+alt+t.
Post back the outputs of terminal commands - Between Code tags, please :
```

sudo fdisk -lu
parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
so we know the type of partitioning and how the hard disk(s) are laid out, and what operating systems are installed where.
Once these are known we can give direction on what it will take to boot ubuntu.

Hopefully[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]
I hope its okay if I post a picture?

[IMG]http://i.imgur.com/HvDM3cz.jpg[/IMG]

Thank you for your reply. :)

---

### Post by Bashing-om on 2015-01-22
Leevi_Hiekkinen; Hey !

That says that ubuntu is installed - as the sole operating system - on the hard drive.

Baby steps:
Reset in bios to boot that 1st hard drive (sda);
As soon as the bios screen clears depress and hold the right -shift- key

Do you get the grub boot menu ? Default time out is 10 seconds, if you wait the 10 seconds 

What results ?

[INDENT][INDENT]it all in the process
[/INDENT][/INDENT]

---

### Post by Leevi_Hiekkinen on 2015-01-22
> **Bashing-om said:**
> Leevi_Hiekkinen; Hey !

That says that ubuntu is installed - as the sole operating system - on the hard drive.

Baby steps:
Reset in bios to boot that 1st hard drive (sda);
As soon as the bios screen clears depress and hold the right -shift- key

Do you get the grub boot menu ? Default time out is 10 seconds, if you wait the 10 seconds 

What results ?
[INDENT][INDENT]it all in the process
[/INDENT]
[/INDENT]
Hey.
When I boot into the hard drive it gives me a black screen that says "verifying dmi pool data". Also, when I try to get into the grub boot menu it doesn't appear.

---

### Post by Bashing-om on 2015-01-23
Leevi_Hiekkinen; Hey;

Sorry for the delay in responding. I am awaiting others to also respond.
It is a no no to respond to a thread with nothing constructive to add, but .....
I think - and I could be wrong - that " verifying dmi pool data" is a bios thing and has nothing to do with the operating system. It could be that bios is having a problem handing off to the boot code ?

in this instance I
[INDENT][INDENT]just do not know
[/INDENT][/INDENT]

---

