---
title: "Installation difficulties with PowerPC G4 iBook"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by iangarforth on 2012-02-25
Hi all,

I can't get to boot from CD on my wife's PowerPC G4 iBook.  It may be that I'm just holding down the wrong key or something, but I also wonder whether my disk is wrong, which is called the i386 disk.  Do I need something different for this chipset?

---

### Post by winh8r on 2012-02-25
There is a helpful guide here:

[https://wiki.ubuntu.com/PowerPCFAQ#Is_Ubuntu_supported_on_PowerPC.3F]("https://wiki.ubuntu.com/PowerPCFAQ#Is_Ubuntu_supported_on_PowerPC.3F")


Apologies if you have already been there!

---

### Post by Lars Noodén on 2012-02-25
You need to hold down C while booting and it will boot from the CD.

As to which CD you need, x86 won't run, you've got a better chip.  You need one of the ones with **powerpc** in the filename.  Here is the oversized Ubuntu:

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

Here is Lubuntu, which will fit on a regular CD/CD RW:

[http://cdimage.ubuntu.com/lubuntu/daily/current/](http://cdimage.ubuntu.com/lubuntu/daily/current/)

If necessary, it is possible to turn Lubuntu into Ubuntu by adding the package ubuntu-desktop

---

### Post by asifnaz on 2012-02-25
you need **powerpc iso** not i386 one

---

### Post by iangarforth on 2012-02-25
Thanks all

The Minimal CD is now installing but it then doesn't find a driver for the hard drive, and therefore cannot continue with the installation.

It gives me a list to choose from, but I don't know how to select this.  How can I find out which driver it is?  And does this have anything to do with the fact that there's only one partition on there?  I was assuming I'd go into GPartEd in order to sort an ubuntu partition during the installation..?

---

### Post by Lars Noodén on 2012-02-25
I vaguely remember something like that on one of my installations.  Try just ignoring it and it might do just fine.

---

### Post by iangarforth on 2012-02-25
:( Sadly not...

It then goes on to the next stage which is partitioning, and then stops because it doesn't have anything to partition.

I'm surprised, really - I wouldn't be surprised if a Windows box did it, in that it might have who knows what hardware in it, but in a Mac with the same old hardware, I thought it would pick it up.

Anything else I can try?  Other seems to have had success switching it to Master rather than Slave, but I don't know how to do this in a system without BIOS?

---

### Post by Lars Noodén on 2012-02-25
If the list of drivers is short, you could try walking through them till one works.

---

### Post by iangarforth on 2012-02-25
Ok, it took most of a day, but I did it.  Sort of...

Turns out it's a known bug in 11.10.  The answer is to install 11.04, then upgrade.  11.10 lacks a key driver that will apparently be put back in for 12.10.

Problem now is I can't repartition the drive.  The installation won't do it, and I can't work out how to do it without the OS disks which my wife doesn't seem to have.  Unless anyone can suggest anything?

---

### Post by Lars Noodén on 2012-02-25
Strange.  I've been able to repartition the drive during the installation, but then I am using the test versions of 12.04.  Do you have the discs that came with the machine?  You could boot up from the disc and then use the Disk Utility to repartition.

---

### Post by iangarforth on 2012-02-25
> **Lars Noodén said:**
> Strange.  I've been able to repartition the drive during the installation, but then I am using the test versions of 12.04.  Do you have the discs that came with the machine?  You could boot up from the disc and then use the Disk Utility to repartition.

No.  I seem to be stuck in the centre ground of difficulty between the PPC architecture and an unexpected bug.  I can't use the regular desktop install like on a normal Mac, which I've done without problems, and the mini disk seems to go fine but doesn't have HFS+ support in the partitioner.

10.4 on the Mac seems that it won't repartition without the original disks which we don't have.

Rubbish.  Gutted...

---

