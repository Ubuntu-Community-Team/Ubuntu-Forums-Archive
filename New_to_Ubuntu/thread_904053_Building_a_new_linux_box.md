---
title: "Building a new linux box"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Deedlit on 2008-08-28
I just got some parts together to try and build myself a new computer.  The case and CPU are from a Dell Optiplex GX1.  The hard drive is 160 GB.  I put the live cd in and it worked just fine.  But when I reboot after installation I get an error 18 while GRUB loads.  After some research it says that that the problem seems to be with the larger hard drive.  Is there a way I can force it to accept this hard drive?

---

### Post by erichmj on 2008-08-28
I believe you need to download the alternate cd to install with LVM support.

---

### Post by tamoneya on 2008-08-28
look near where the harddrive is connected to the ribbon cable.  There should be some pins that have jumpers on them.  There should be information on the harddrive itself telling you how to use these jumpers and there should be a setting for setting the drive to smaller size for better bios compatibility.  You will then get all the space when you are running ubuntu.

---

### Post by mike1234 on 2008-08-28
Have you upgraded to latest bios version? I had to flash my Dell bios for an unrelated issue once.

M.

[http://support.dell.com/support/downloads/driverslist.aspx?os=LNUX&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=PLX_PNT_PII_GX1&hidos=WW1&hidlang=en&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?os=LNUX&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=PLX_PNT_PII_GX1&hidos=WW1&hidlang=en&TabIndex=)

---

### Post by Deedlit on 2008-08-28
I figured I would have to flash the BIOS but the problem is I don't have a floppy drive or disks so I am trying to see if there is a way I can first; install the flash info onto my USB and second boot straight from the USB.

---

### Post by mike1234 on 2008-08-28
> **Deedlit said:**
> I figured I would have to flash the BIOS but the problem is I don't have a floppy drive or disks so I am trying to see if there is a way I can first; install the flash info onto my USB and second boot straight from the USB.

 You can always "waste" a cd. Terrible waste of space but if you really need to.....:)

M.

---

### Post by Deedlit on 2008-08-29
Okay, moved the jumpers and reinstalled. After reboot, same error 18.

---

### Post by panhandle on 2008-08-29
I take it you have seen this site: 

[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)


Specifically the following: 

>  Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.


---

### Post by confused57 on 2008-08-29
Here are some possible solutions for grub error 18:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

What I would recommend is delete your current partitions, select "manual" partitioning when reinstalling...select new partition of approximately 15 Gb at the beginning of the drive, primary, ext3, mountpoint /

Then the rest of the hard drive, except for about 1.5 Gb at the end of the drive, select logical(or extended), ext3, mountpoint /home

For the remaining 1.5 Gb, select logical partition, mountpoint swap.

---

### Post by HieroPosche on 2008-08-29
From what I'm reading, the previous poster (beat me to it) is correct.  The boot partition should solve that problem. Just a small partition to store the kernel and then you can access the rest of the drive normally.

Alternatively, and I'm not sure this is the case based on your post, but if you're running the 160gig HD along with a smaller primary drive, you could install the OS on the smaller drive and see if that functions.  But again, I'm not sure if that's the case so the previous suggestion should solve your problem either way.

Let us know how it turns out for ya.

---

