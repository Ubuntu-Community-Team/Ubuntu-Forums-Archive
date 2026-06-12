---
title: "Computer won't boot live cd after failed format of hd"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by palikir on 2014-08-08
Hi all,

I have installed ubuntu 14.04 on my pentium III computer, which worked. 
However i tried to install Win98 on it, and thus let win98 format my hd. However the HD was NTFS instead of fat32, so the format failed.
After the error, when i tried to restart the pc i got in the grub mode with the error:

"error : no such device : 82f5d694-9e69-4656-8193-e616f2b66a20.
 grub rescue>"

When i insert the live cd in the dvd drive, it doesn't show any difference and goes automatically to the grub rescue mode & same error.
I used multiple distro's of linux and none seem to make any difference. 

When i use the windows98 installation disk, i have the option to boot from cd, or from the hard disk. 
If i boot from the hard disk, it gives again the same error. 
 If i boot from cd, i can use it, however it is not compatible with the HD, so i can't install it, or read its content.

My question is, how could i start up ubuntu again or format my HD to fat32.

With kind regards,

---

### Post by oldrocker99 on 2014-08-08
The way to dual-boot with Windows is to install Windows 98 **first**, which will format the whole drive as FAT32. Then install whichever Ubuntu flavor you want, and select "side-by side." It will keep your FAT32 formatted that way, and format the Linux partition as ext4.

---

### Post by mörgæs on 2014-08-08
Welcome to the fora.

Windows 98 has been out of support for many years so it's a major security risk. The bad guys have had plenty of time to learn how to break in. 

If you want to use a Pentium 3 I suggest Lubuntu 14.04.1.

---

### Post by coffeecat on 2014-08-08
If you can boot from the Windows 98 CD and the Ubuntu DVD no longer boots when once it did, then the logical conclusion is that the Ubuntu DVD has been damaged. I suggest you burn a new Ubuntu DVD and try that or, as mörgæs suggests, a lighter variant such as Lubuntu.

---

### Post by bradwilliams923 on 2014-08-12
If these options fail, there is a live CD you can download called Gparted Live, which will give you a live instance of Gparted to reformat your hard drive however you like, as well as attempt to make file system recoveries or repairs as needed. If you plan on dual-booting, I would recommend setting up your partitions ahead of time through the os installers or Gparted, and always install Windows first. But I hope you plan on using Windows 98 just for fun and nostalgia, and without an active internet connection. ;-)

---

### Post by JKyleOKC on 2014-08-12
> **coffeecat said:**
> If you can boot from the Windows 98 CD and the Ubuntu DVD no longer boots when once it did, then the logical conclusion is that the Ubuntu DVD has been damaged. I suggest you burn a new Ubuntu DVD and try that or, as mörgæs suggests, a lighter variant such as Lubuntu.Good suggestion, but the OP's message indicates that his machine is trying to boot from the hard disk, and since it cannot locate the Grub files due to the later Win98 reformatting, stopping there. This suggests to me that a repair of the MBR, removing the Grub code and putting back the quite simple Win98 bootloader, might be a solution.

If he can boot the Win98 installation CD, then re-installing Win98 and telling it to reformat the disk ought to get things back to a point at which he could then re-install Ubuntu from the DVD. As I recall, Win98 didn't have built-in DVD drivers and definitely had no capability to boot from a flash drive. However, just getting the MBR fixed might solve the problems for him.

---

### Post by bradwilliams923 on 2014-08-13
Looking at the OP, it's unclear if he's trying to dual-boot Win98 with Ubuntu, or replace Ubuntu with Win98. I have to assume it's the dual-boot option, in which case I don't see why the ext4-formatted drive can't just be reformatted to FAT by Win98. But if it can't because of the ext4 format, then using the Ubuntu live DVD he should be able to run GPartEd, delete the HD partition, create a new partition table and set up his separate partitions, and then run the Win98 CD for installation. Am I right in thinking the Ubuntu DVD carries GPartEd on it?

---

### Post by mörgæs on 2014-08-13
OP has been passive for five days. Let's wait for his return before we continue here.

---

