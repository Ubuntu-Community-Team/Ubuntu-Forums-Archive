---
title: "Trying to Recover Windows 7 for dual boot"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by shwaydogg on 2012-12-09
I have installed ubuntu 12.10 on a Eee PC Flare Series.  I am trying to get dual boot working, however I may have ruined my windows 7 install.  

On my first attempt to install ubuntu, I had the windows partition as the swap drive.  Of course, this was a mistake.  But I do not believe that it ever had the chance to be used for swap besides whatever the install did.  

That first install did not work.  I did another instaell and told the install to no longer use the windows partition as swap.

Here is my boot-repair output: [http://paste.ubuntu.com/1421607/](http://paste.ubuntu.com/1421607/)

Now when GRUB comes up there is an option for "windows recovery" which launches successfully but when I proceed with that process it restarts the computer and I come back to square one at the GRUB screen.

My home is that the windows boot was not truly affected and I can get it into grub menu.  Any hope?

---

### Post by Mark Phelps on 2012-12-09
You said you used the Windows partition as swap -- which implies you reformatted it.

In some cases, preinstalled Win7 machines come with two different partitions (at least). One contains the boot loader files, the other (much larger), the OS.

IF you only overwrote the bootloader partition, you could then reformat that and use boot-repair to get the Win7 boot files back.

But ... if you overwrote the Win7 OS partition, that stuff is gone.  There are Win7 data recovery apps that might be able to allow you to get some files back, but you would have to remove your drive and connect it to a Win7 PC to do that.

---

### Post by shwaydogg on 2012-12-09
I did set sda2 the Win7 OS as the swap partition on my first install.  I do not care about any personal files though.  I would just like to get win7 booting again if possible.

---

### Post by oldfred on 2012-12-09
If swap was used at all you have damaged Windows. If it was just data you might be able to get some data back. But as a system any missing/damaged file may corrupt entire boot.

But you can use Disk Utility, click on sda1, & Edit Partition in Ubuntu to convert sda1 from swap to NTFS or 07 type. That will not reformat it but just change it type in the partition table. Then you may be able to at least use Linux to look at it and see what it says.

---

