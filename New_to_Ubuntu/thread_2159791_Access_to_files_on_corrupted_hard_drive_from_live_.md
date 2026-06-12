---
title: "Access to files on corrupted hard drive from live CD"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by DJToman on 2013-07-04
This should be pretty basic.

I want to do a clean install on a corrupted hard drive that contains a home folder I want to preserve. I can boot from and run a live CD and can see the material I want to copy to a USB flash drive for later transfer. 

How do I set permission to copy the Home folder to the USB? If I mount the desired material and attempt to copy it, I get an error message telling me that I don't have permission.

The operating system on the existing hard drive is corrupted, so I can't simply boot into and run off of it.  How do I tell Nautilus on the hard drive the root password while I'm running from a live CD?

DJToman

---

### Post by ajgreeny on 2013-07-04
Start your file manager in ubuntu live system with command ```
gksudo nautilus
``` and then you will be able to copy the files to your USB drive.

---

### Post by Mark Phelps on 2013-07-04
> **DJToman said:**
> ... I want to do a clean install on a corrupted hard drive...

What do you mean by "corrupted"?

How did it get "corrupted"?

If the actual problem is bad sectors, then you're wasting your time and setting yourself up for disaster.  While modern drives can recover from an occasional sector problem, if the sector faults are growing, the drive is dying -- and it could last only a few days, or hours.

Also, even though you might be able to install to it today, if the hardware is failing, there's no guarantee that it will boot, or work, tomorrow.

---

### Post by DJToman on 2013-07-04
Mark Phelps,
Sorry...the drive is not corrupted. The installation is. It became corrupted when I tried to do an online upgrade...always a dicey proposition. I can't boot from the hard drive. I get gibberish. The Home directory I want to copy and all the files on it are visible from a live CD session and uncorrupted. I need to be able to copy from the live CD session so that I can wipe the disk and start fresh and then copy my old Home directory into the new installation.

---

### Post by Zill on 2013-07-04
> **DJToman said:**
> Sorry...the drive is not corrupted. The installation is. It became corrupted when I tried to do an online upgrade...
Which is exactly why the [Upgrade Ubuntu webpage]("http://www.ubuntu.com/download/desktop/upgrade") clearly states at the beginning:
> We recommend you backup your existing Ubuntu installation before updating.
A good backup saves a lot of problems later on. ;-)

---

### Post by DJToman on 2013-07-05
Thanks. That's helpful for the next time. 

...and this one?

---

### Post by dannyboy79 on 2013-07-05
have you mounted your external USB drive (where you want to store your data to) somewhere it's writable? If it auto-mounted in /media/ then it's possible that directory is owned by root.

 Did you mount your existing /home/ folder somwhere you can access it?

---

### Post by DJToman on 2013-07-05
Problem solved.
It was necessary to download and install hfsplus and libhfsp0 to the live CD session to be able to get at permissions after doing "sudo nautilus."
Once permissions were set, copying proceeded with no difficulty.
Thanks all.

---

### Post by ajgreeny on 2013-07-07
What a shame you did not mention that there was an hfs+ partition involved.  We could have answered your question much more usefully if we had known.

---

### Post by Handssolow on 2013-09-10
> **ajgreeny said:**
> What a shame you did not mention that there was an hfs+ partition involved.  We could have answered your question much more usefully if we had known.

Perhaps this opinion might mislead some.

I have a SSD which looks to be failing and am now currently copying files off to a usb stick before a RMA back to Samsung. I have used it for about a month and have already formatted and re-installed 12.04 because of file corruptions. Using a live CD I was unable to use gksudo nautilus to copy because of file permissions. With live 12.04 CD and internet connection I installed hfsplus (sudo apt-get install hfsplus) then using gksudo nautilus again, I was able to copy across the files. I'm about to have another go with fsck but at lease if things go belly up I've got copies of the important files.

I've no Apple or Mac files on the SSD, no partitions other than what a fresh install of 12.04 would create (ex4 etc), just some rather important Oblivion files.

Update
After running fsck from a live CD, I managed to get 12.04 to boot up. Looking in Log File Viewer, the error messages in syslog pointed to a Sata cable fault. Once replaced, fsck reported no faults and the PC seems back to normal. It looks like there was no fault with the Samsung SSD, only with the cable.

One minor point. In copying the 12.04 Documents directory it changed the original ownership to root on the PC. This was easily corrected with gksudo nautilus.

---

### Post by Jonathan Precise on 2013-09-10
Please mark this as solved by going to thread tools.

---

