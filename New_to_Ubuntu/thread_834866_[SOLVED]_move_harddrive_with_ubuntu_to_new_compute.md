---
title: "[SOLVED] move harddrive with ubuntu to new computer?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-06-19
so i have a computer that has only one IDE slot and four SATA slots

i dont have any SATA devices available to me now, only an IDE harddrive and an IDE cdrom

also i have no flash drives available


so basically my newbish question of the day is can i put the harddrive in an old computer to install ubuntu from the live cd, then move it to the new computer 

or are there alot of driver and compatibility issues that i would run into?

---

### Post by overdrank on 2008-06-19
> **tjwoosta said:**
> so i have a computer that has only one ATA slot and four SATA slots

i dont have any SATA devices available to me now, only an ATA harddrive and an ATA cdrom

also i have no flash drives available


so basically my newbish question is can i put the harddrive in an old computer to install ubuntu from the live cd, then move it to the new computer 

or are there alot of driver and compatibility issues that i would run into?
HI and you can do this but the only issue you may encounter is the xorg it the graphics are different on the systems. If you have ata hard drive and cd drive cant you use them as master and slave on the system that you want to transfer to, and do the install on the permanent system?

---

### Post by Dynaflow on 2008-06-19
This sounds like one of those logic puzzles from elementary school.

You might also be able to do a network install if you have a couple of computers and a router handy:  [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by tjwoosta on 2008-06-19
> If you have ata hard drive and cd drive cant you use them as master and slave on the system that you want to transfer to, and do the install on the permanent system?

i dunno, can i?

i didn't realize i could put a cdrom drive inline with the harddrive

i always just assumed i would need to have two seperate ide slots

---

### Post by overdrank on 2008-06-19
> **tjwoosta said:**
> i dunno, can i?

i didn't realize i could put a cdrom drive inline with the harddrive

i always just assumed i would need to have two seperate ide slots

If you have a ide cable with 3 connections then one attaches to the mainboard the middle is for the slave and the end is for the master. The master is the one with the second connector closest to it. You will have to set the jumpers on the drives accordingly.

---

### Post by cariboo on 2008-06-19
You should have no problems as long as you make sure you've got the jumpers set right. The hard drive should be the master and the CD drive the slave,when you connect the cable to the drives connect the hard drive to the first connector and the cd drive to the connector on the end of the cable.

If those are the only drives in the computer they should be setup that way already.

Jim

---

### Post by tjwoosta on 2008-06-19
ok, thanks guys

yea i know how to setup the master and slave, i just always assumed you could only have hardrives on one cable and cdroms on another (i didnt realize i could mix and match)


and the computer was given to me without any drives (i had the IDE drives in an old computer)

---

