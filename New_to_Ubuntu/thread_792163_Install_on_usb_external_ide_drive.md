---
title: "Install on usb external ide drive?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by tsantsa31 on 2008-05-12
Ok, I just built up myself another pc. 750g hdd, 3 ghz wolfdale dual core pentium, evga nvidia 8800gt, you know, the works...well, the less than $1000 works!

I don't want to partition my harddrive, but I have an external ide reader and a couple of harddrives that I am going to use for storage.  Well I was wondering if on one of these drives can I install ubuntu?

If so, how do I get it to boot up?  If I have the drive disconnected at bootup will grub try to boot into it or skip it all together?

I looked in the forums but some of these answers seem to be buried in long threads, if someone can link me to a guide that would be great!

TIA

---

### Post by bodhi.zazen on 2008-05-12
You have a few options, depending on how much you time / effort you want to put into it ...

Easy : Ubuntu only requires 5 Gb, so giving 10-15 Gb for Ubuntu + a swap partition ( 1 Gb ) plus a dedicated storage partition would be the way to go, IMO at least. It is not as if you are tight on HD space ....

Moderate : Does your BIOS allow you to select which hard drive to boot from ? If so, boot from the external hard drive and install GRUB into the MBR of the External Hard drive. If you BIOS allows this will not be too hard.

Harder : If your BIOS will not allow you to select whic device to boot from, and you do not want to touch your hard drive, install Ubuntu to the second hard drive, install grub to the Ubuntu partition, and then boot from the Ubuntu CD or a grub floppy.

Useful links :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Select an option and we can help with the details if needed.

---

### Post by tsantsa31 on 2008-05-12
Cool, thanks for the quick reply. 

I'll read through the links and decide my options.  I like the moderate option you've proposed the best. I have to look at my bios right quick to find out what I can do.


EDIT: BTW, the mobo is a Gigabyte Ga-P35-DS3L. I think its an Award bios.

---

