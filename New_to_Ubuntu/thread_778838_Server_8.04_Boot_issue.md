---
title: "Server 8.04 Boot issue"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Martink149 on 2008-05-02
Hi All,
 Just installed Ubuntu Server 8.04 on a new Fujitsu Siemans computer. However it will not boot. I have checked the forums and found a load of potential answers but they didn't fix my issue unfortunately. I think it may be to do with using an SATA300 drive? Or perhaps dodgy ram? But more likely something really simple I simply don't know because its my first Ubuntu install. Below I have listed all the things I tried to make this post useful for others and hopefully be of use to another member of the community in pointing me in the right direction.

When loading the boot sequence it simply doesn't think there is any OS on the drive.

When tryng to the "boot from first hard drive" from the boot CD I get :> isolinux: disk error 01, Ax – 0201, drive 80

Which is rather annoying. From checking the forums I heard this can happen when the primary drive isn't flagged as Boot. However, mine is.

Another post said it can happen when the PC tries to boot from a CD drive rather than the hard drive. So I unplugged the CD drive just incase which made no difference.

Another post said it was to do with the jumper settings, however my hard drive is SATA300 (aka SATA II). 

Using the Desktop Live CD seems to work which is nice. I did the hardware test ok in there. 

The server install CD validity test comes back ok.

The ram test from the Server CD doesn't seem to come back with anything, it just waits. There is no error message but no success message either. Sorry, I haven't used it before so not sure if that is bad? 

Cheers!

---

### Post by nowshining on 2008-05-03
maybe you need a new HD.

---

### Post by Martink149 on 2008-05-07
Thanks, I tried another HDD. I also tried CentOS with grub but no luck.

I think it is to do with the very annoying PXE PROM bootloader [http://www.bootix.com/home_en.html](http://www.bootix.com/home_en.html) I have submitted a support request request with them as there is nothing in their FAQ. In their news it says Linux support coming soon, in their FAQ's it has some stuff on linux.

The bios will not let me change to just boot from HDD I have to use this darn bootloader which seems rather M$ centric.

---

### Post by dstew on 2008-05-07
What is the bootloader you are referring to? Can you get into your BIOS setup screens?

To get some more ideas about your setup, boot the Live CD, and open a terminal window (Applications --> Accessories --> Terminal). On the command line enter```
fdisk -l
```Post the result to the forum.

You can try to boot your Ubuntu install from a grub shell once we have a good idea of your disk partition setup.

---

### Post by jimv on 2008-05-07
> **Martink149 said:**
> Thanks, I tried another HDD. I also tried CentOS with grub but no luck.

I think it is to do with the very annoying PXE PROM bootloader [http://www.bootix.com/home_en.html](http://www.bootix.com/home_en.html) I have submitted a support request request with them as there is nothing in their FAQ. In their news it says Linux support coming soon, in their FAQ's it has some stuff on linux.

The bios will not let me change to just boot from HDD I have to use this darn bootloader which seems rather M$ centric.

PUnch it in the head.

---

### Post by Martink149 on 2008-05-07
Cheers all,
 Finally Cracked it!!

After going through the "press 1 for M$ X, press 2 for M$ XX" style documentation and the helpful venors site recommendation to create a Floppy disk. Surely the vendor knows that the server doesn't have a floppy drive! Putting one in is easy enough, but anywhoo..

The RAID controller (or driver) was not linux compatible, but that is fine I just disabled the RAID functionality in BIOS along with AHCI Enchanced (not sure what it is.. helpfile said it was for WinXP). There are rumors of a compatible driver, but I'm not intending to use RAID for now or spend another week tring to set this darn thing up ;-)

Hopefully this will post will be of use to somebody. With that in mind a few notes / learnings - the server is a Fujistu Seimans Econel 100 S2. Don't use the dodgy ServerStart "automated" installation for the install but it does have docs on it. The docs are also on a seperate CD that comes with it. The remote install software they encourage you to use requires an SQL server. The ServerStart CD is not Ubuntu compatiable and you have to agree to a M$ licence to install Linux!!? 

Thanks again.

---

