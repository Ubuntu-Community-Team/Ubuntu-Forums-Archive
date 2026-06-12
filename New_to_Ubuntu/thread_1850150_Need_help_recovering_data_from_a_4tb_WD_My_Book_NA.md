---
title: "Need help recovering data from a 4tb WD My Book NAS"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by wildfirez98 on 2011-09-25
Hi guys/gals!

I'm running Ubuntu 11.04 64-bit and recently my friend asked for my help because he has a Western Digital 4tb (4 x 1tb) NAS that crashed on him and the Western Digital folks were asking him if he has a Linux computer he could use for troubleshooting (hence where I come in).  I'm not experienced with NAS's at all but everything is setup in a Raid 5 (mirrored I believe array).  So I would take each drive out, check it in disk utility (seems to mount okay) and then I'd go to /mnt/media to check for any data and I'd pull up some information but it was far from recovering anything.  So I guess I need some guidance here, can I even recover any of my friends data by hooking up one drive at a time or am I flawed in my logic in that I need to somehow mount the whole array and try to recover the data that way?  If i get some more SATA cables I could hook up everything to my PC and try mounting an array to recover?  

Ah anywho any guidance or advice on where to start would be appreciated.  My friend does not want to spend thousands of dollars to send these drives into WD for recovery.  Since I can seem to mount them and Ubuntu recognizes their in an array I'd think somehow I could I just don't know where to start.

Thanks to any and all in advance for reading/helping with this.

---

### Post by Denver Dave on 2011-09-25
Might try booting the problem PC with a ubuntu boot dvd or usb and see if the PC can recognize the problem hard drive.

Another trick that I've used with windows PCs is to put the drive in an external case that plugs into a usb port on a functioning PC (maybe 40 bucks for the case).  Sometimes even if the original PC won't boot from the HD, another PC can read the drive and you can at least access your data.

Also there may be a way to get some sort of windows rescue disk

Good luck

---

### Post by tgalati4 on 2011-09-26
It's my understanding that the MyBook uses a proprietary, or tweaked RAID5 configuration.  I doubt you would have much luck with recovery without special tools to read MyBook arrays.

How did the NAS crash?  Was it a single disk failure or a NAS controller failure?  I would build a [http://freenas.org](http://freenas.org) box and put the drives in it and see if they can be recognized as a valid RAID5.  You won't have much luck with pulling data off of single drives because the data is striped across the drives in tiny little pieces.  If you know that one drive is bad (because it makes a sickening, scratching noise), then you could (in theory) replace the drive and the NAS would automatically rebuild the array based on the checksums, which are also stored across the drives.

If the RAID5 failed during a recovery operation, which takes several hours, then you have definitely lost data.  That's the downside of using RAID5 with large disks.  Originally RAID5 was specified with small hard disks (less than 80 GB) and it worked OK with disks of that density.

RAID5 is not a backup solution, but a speed and uptime improvement scheme--unless the NAS fails then you don't get either speed or uptime.

---

### Post by wildfirez98 on 2011-09-26
So my friend spoke with WD level support today and basically they said  you'll need to hook-up all 4 drives into your PC and see if Ubuntu  recognizes the RAID array and try to recover data from there.  I have  the open ports in my motherboard so once all 4 drives are hooked up I  should fire up Ubuntu and hopefully all the drives automount and I can  see the data correct?

---

