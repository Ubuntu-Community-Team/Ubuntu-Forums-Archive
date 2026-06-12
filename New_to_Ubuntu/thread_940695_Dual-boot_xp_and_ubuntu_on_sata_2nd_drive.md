---
title: "Dual-boot xp and ubuntu on sata 2nd drive"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by deerewright on 2008-10-07
I had some problems getting ubuntu and xp to both boot, but I got ist solved.  I am posting here in hopes someone can explain to me what went wrong, and to help anyone else with the same problem. (I am doing this from memory, so I hope I get it all right.)

Okay, here is my setup:

I have a desktop that I built with a GA-K8N pro sli MB.  I have gone through several different drive setups over the years, but had my system drive starting to fail, so I replaced it with a new SATA drive.  I do not have a RAID setup.  My current setup is one ATA IDE drive on primary master just used for data storage, and then my system/boot drive is on the first SATA port.  I had to tell the bios to boot from the 1st SATA drive.  It is partitioned as such:

> |  WINDOWS(NTFS, pri,act)  | APPS (NTFS, pri)  | DATA (NTFS)  |  UBUNTU (EXT3)  |  /home (EXT3  |  SWAP  |

From DATA on is in an extended partition, so the extended partition becomes partition 3, DATA 4, UBUNTU 5, etc.

I had windows already installed, then installed ubuntu using manual partitioning to setup my drive as above.  When grub installed it originally looked like this:

> title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cea0b652-867c-48cc-82f6-e929ef2c5974 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cea0b652-867c-48cc-82f6-e929ef2c5974 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

When it first reboot It tried to boot ubuntu but I got an error message something like error reading stage2.  So I reboot, the manually edited the ubuntu line to read "root		(hd0,5)" instead of (hd1,5). (I think grub read my IDE primary master as drive 0, and my SATA 0 as drive 1, but when the bios is set to boot off of SATA 0 it reads it as drive 0???)  That worked and ubuntu booted fine.  So...I thought, "I just need to change Windows to (hd0,0)".  I did and then I had all kinds of problems.  I'm not sure what happened, but I think the manual partitioning messed up my MBR or partition table.  I booted from my Windows XP Pro install disk, recovery, and did a "fixboot". Now, I could boot into windows, but no grub; it was back to the windows loader.  

I popped in the ubuntu 8.04 live cd and reinstalled grub.  This time it looked like this:

> 
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cea0b652-867c-48cc-82f6-e929ef2c5974 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cea0b652-867c-48cc-82f6-e929ef2c5974 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Again, ubuntu would boot, but not windows. (I wish I could remember the error messages, but I can't.)  The way I got it to work was to change the windows grub entry to this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)

root		(hd0,0)
makeactive
#savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

My questions are what are the "map" commands doing, why are they there, and how in the world would a complete newbie ever figure this out?

Also, I know it will also work without commenting out the "savedefault" line, but can somebody explain to me exactly what that does?

Sorry, this got so long, but, hopefully this will help someone else out there.

---

### Post by Pelham123 on 2008-10-07
This page is more informative than I could ever be:

[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_OS_entries](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_OS_entries)

---

