---
title: "Trouble installing Ubuntu 7.04"
date: 2007-10-09
forum: Oklahoma Team - US
---

### Post by vertigo_ok on 2007-10-09
Howdy!

I've run into a bit of a problem installing 7.04. I have run Ubuntu on a virtual drive in WinXP Pro and decided to wipe my laptop and go completely Ubuntu. Burned a CD from my desktop and got it to boot on the laptop (juggled the boot sequence around).

Flash screen loads, I choose "install" option. Bar goes back and forth then stops, goes to a prompt and tells me "[large integer] Buffer I/O error on device FD0, Logical Block 0" over and over.

Caught wind on the forums elsewhere that this may be due to my CD drive is a CDRW. The only other option for my laptop is a modular DVDROM that it wouldn't let me boot from.

Any ideas? Ever run into this before?

-j

---

### Post by palintheus on 2007-10-09
hmmm, I haven't seen that before. Are you using the LiveCD or the Alternate CD?

---

### Post by Malh on 2007-10-09
same problem, live cd

---

### Post by palintheus on 2007-10-09
you may try the alternate cd, I had to use that on my laptop as the livecd did not like the Santa Rosa chipset.

---

### Post by vertigo_ok on 2007-10-10
Ok, so I got the alternate CD. Ran the installation process. Formatted my HD (one partition for install to ease changing distro if desired, one for files) not that any of that matters because...

my CD had an error  Is that common? I know that Gusty is coming out soon, so I figured Feisty would be pretty stable. Am I incorrect? Should I try Edgy? Should I redownload the alternate CD and burn it again? I burned it on 40x in Nero.

As it stands, I've got a brick laptop ^^'

The .iso for the alternate CD came from a torrent because it was faster - getting it again from ubuntu.com

---

### Post by vertigo_ok on 2007-10-10
HORRAY!!

Official site's Alternate CD worked, but I have a question. I don't know enough about Linux to figure this out. I formatted my 30GB HD into two parts, but it seems that Ubuntu only sees one of them. How do I get it to find the other?

---

### Post by palintheus on 2007-10-10
can you post or attach your the contents of your fstab?

also if you have access, there is usually a couple of us in #ubuntu-oklahoma on IRC.

---

### Post by vertigo_ok on 2007-10-10
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a83ba938-e14b-4dcd-b7f2-18865f1c6cbe /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=2f3e24b0-dc93-4f57-a127-7750a13d2d4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

There's my fstab. So, I found out what an fstab was :) Horray for learning. 

Does it matter what network I connect to the IRC channel in? I'm familiar with IRC but not terribly savvy with it. I am accessing it through Chatzilla in Firefox, not that it matters.

---

### Post by palintheus on 2007-10-10
hmm, not sure, you may trying installing gparted and then seeing if there the partition just needs to be formatted 

we are on freenode, which if I remember right, when you open chatzilla, it presents you with several options on networks, just click on freenode, then in the input box type "/join #ubuntu-oklahoma"

---

### Post by J11Gyro on 2007-11-02
Wish I could help but I installed on two different drives.

---

