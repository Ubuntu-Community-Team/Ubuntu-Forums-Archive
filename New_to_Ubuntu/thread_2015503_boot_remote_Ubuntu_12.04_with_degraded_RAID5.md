---
title: "boot remote Ubuntu 12.04 with degraded RAID5"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by dvks on 2012-07-03
I have a remote Ubuntu 12.4 system, which means that it should be able to restart automatically without any keyboard or terminal.
I have the following hard drives configuration:
HD partitions /dev/sda1, /dev/sdb1, /dev/sdc1 are "user data" drives arranged in RAID5
HD /dev/sdd not used at this point but installed on the system
HD /dev/sde is the Ubuntu system drive and it does not participate in the RAID5.
 
While the system is running I simulate RAID 5 drive failure by pulling out drive /dev/sda
The RAID 5 becomes degraded and continue to function with no problems.
 
But........
 
If I shutdown the system and restart it, it will come with a message that the RAID5 is degraded and boot into initramfs prompting for user input instead of booting the system with the degraded RAID, if I exit the initramfs it will continue to boot with the degraded RAID 5.
 
The following steps didn't resolve the problem:
1. I modified /etc/initramfs-tools/conf.d/mdadm to have the line: BOOT_DEGRADED=true
2. Just to make sure I also ran: sudo dpkg-reconfigure msadm and set the boot degraded otion through this tool too.
3. During boot I 
 
The above didn't help and the system continue to boot into initramfs
 
Appreciate your help

---

### Post by SlugSlug on 2012-07-03
just signing up to this :popcorn:

---

### Post by dvks on 2012-07-03
one more detail that I just noticed and I am not sure if it is important or related:
When I boot the system with a monitor and keyboard the top of the GRUB boot screen shows: [FONT=Calibri]GNU GRUB (version 1.99-2.1ubuntu3.1)[/FONT]
[FONT=Calibri]Shouldn't it be GRUB version 2?[/FONT]
[FONT=Calibri]Does version 1.99-2.1ubuntu3.1 have the bootdegraded option?[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]I tried to setup a kernel argument [FONT=Calibri]bootdegraded=true during boot but failed to do it either because I am doing something wron or the GRUB version is not correct or this is not needed anyway since the system is installed on another drive not on the RAID5[/FONT][/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT]

---

