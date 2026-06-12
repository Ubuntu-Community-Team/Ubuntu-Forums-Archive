---
title: "[SOLVED] unwanted partition of flash drive"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by querent on 2008-07-10
So I've got this old 512 flash drive, and it came with a 1.44 Mb partition designed to look like a floppy drive, and on it is a manual and a .exe file that supposed to control password protection or something.  Every time I mount the flash-drive, it thinks there's two, and this is annoying.  how can I delete this little partition?

it's /dev/sdb and /dev/sdb1 (I think), and fdisk can't see sdb1 (I don't really know how to use fdisk, i admit.)

thanks,
q

---

### Post by querent on 2008-07-10
Oh, there's nothing on the drive.  It can get wiped.

---

### Post by LowSky on 2008-07-10
install gparted

```
sudo apt-get install gparted
```

It will be under System>Admin> Partiton Editor

the program can add and delete partions. you need to unmount the drive before you can edit it's partitions.

---

### Post by querent on 2008-07-10
So i install gparted, but it doesn't see this 1.44 partition.  I assume it's a partition.  when i stick the drive in it mounts /media/disk and /media/disk-1.  gparted thinks the whole drive is 486 mb.

---

### Post by LowSky on 2008-07-10
ok I am stumped as well. I did some testing of my Sandisk Cruzer which is partitoned just like your flash disk, but in my experiment the second partion doesn't show up at all anywhere, except when I am in Windows....hmmmm

---

### Post by LowSky on 2008-07-10
ok I did a little bit of web searching and it seems that these tiny partions can be locked and in some cases cannot be formated away.

If you know the brand try googling > format flash partion linux

---

### Post by querent on 2008-07-10
i'll check it out.  thanks

---

### Post by fatality_uk on 2008-07-10
If it's what I think it is, then that small partition is actually a U2/U3 drive segment. You can get rid of them.

This will only work in Windows. Actually, come to think of it, I have never tried this software in WINE so it might work

Anyway, grab the software from here, delete that pesky U2/U3 segment and boot into Linux and gparted should allow you to format the whole drive

[http://www.sandisk.com/retail/default.aspx?catid=1415](http://www.sandisk.com/retail/default.aspx?catid=1415)

Let us know if that works!

---

### Post by querent on 2008-07-10
the program runs with wine, but asks me to insert a "U3 smart drive".  it doesn't see the flash drive, mounted or no, so I made a 

/home/me/.wine/drive_c/mnt

directory and mounted the flash drive to there, thinking wine would look there, but no go.  does windows expect it to show up somewhere specific?

i could try this on my moms vista machine, but i'd be cool if wine could do it.  windows is where cooties come from.

q

---

### Post by bodhi.zazen on 2008-07-10
Here are a number of links on removing these things :

[http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html](http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html)

        [http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

        [http://cse.msstate.edu/~rwm8/hackingU3/](http://cse.msstate.edu/~rwm8/hackingU3/)


In my experience, in the past, I just formatted the entire drive. More recently I just do not buy these things.

---

### Post by fatality_uk on 2008-07-10
Ok cool, so it is a U3 drive.
I had to run the uninstall app in Windows. I looked, & there's no way to get round it. Download the app, run it in Vista and clear it that way.

bodhi.zazen, that bottom link doesn't work and the other two still require Windows to run the uninstall software.

---

### Post by querent on 2008-07-10
first, thanks all around

ok...none of the programs listed so far have recognized this thing as a U3 device...not through wine and not on a vista machine

I may be an idiot for not having posted this earlier, but i ran the command:

sudo mkfs.vfat /dev/sdb -I

prior to running either of the .exe's suggested.  It still mounts as two, however.

does this change things?

---

### Post by querent on 2008-07-11
hello...?  have i been given up on?

---

### Post by bodhi.zazen on 2008-07-11
I solved the issue by wiping the drive clean. and re-formatting it.

---

### Post by querent on 2008-07-11
forgive a noob, but how?

---

### Post by querent on 2008-07-12
Hello...?

---

### Post by bodhi.zazen on 2008-07-12
> **querent said:**
> Hello...?

You can either do it from the command line or with gparted (graphical)

gparted is on the live CD, but is not installed.

Open a terminal and enter :

```
sudo apt-get install gparted
```

Then ```
gksu gparted
```

You must unomount the usb device, but leave it plugged into the computer. You can do this from gparted as well.

Alternate is to usre fdisk

```
sudo fdisk <device>
```

Then re-format the device to a new filesystem, FAT, ext3, your choice.

---

### Post by querent on 2008-07-12
this has already taken way longer than i anticipated, but i'm frustrated that i can't gain control over my own device.

thanks to everyone, especially bodhi.zazen, for the help so far.

So, there's this:

me@mine:~$ gksu gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/sdc - unrecognised disk label.

/dev/sdc seems to be the offending partition.  gparted shows them both as USB devices, and they're only listed by ls /dev when the thing's plugged in.

each (sdb, sdc) appear totally unallocated under gparted, with sdc at 0.0 B.

i know nothing of fdisk, and can make no sense of it.  i'll go into the man now, buy any quick advice is always helpful.

---

### Post by bodhi.zazen on 2008-07-12
LOL

If all else fails there is always DBAN

Be careful with that thing :

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by querent on 2008-07-12
this looks heavy.  i'm intrigued.  thanks.

---

### Post by querent on 2008-07-13
Victory.  Blessed be.  And know I know of the existence of DBAN (hehehe...)

/dev/sdb
/dev/sdc

both still show up when the drive is in, but, after formating /dev/sdb via gparted, only it automounts.  and the other appears to be size 0.

had to use the beta version of DBAN.  and viman to get back write permissions (even after chown, chgrp...had to do this back before my last reinstall of ubuntu too, so this was not a surprise).

So, thanks again.

---

