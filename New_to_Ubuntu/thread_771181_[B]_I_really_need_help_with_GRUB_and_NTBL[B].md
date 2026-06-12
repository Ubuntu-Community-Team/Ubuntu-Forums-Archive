---
title: "[B] I really need help with GRUB and NTBL[/B]"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by belbakri on 2008-04-26
Hi, 
  putting linux on my pc and dual booting is new to me so forgive me for my ignorance.  I've installed ubunta 8.04 on a scocond hard drive with grub in the / dir (sd1,0).  I'm trying to get the windows bootloader to boot linux.  I've followed alot of the help on the net.  Here's what I've done :

1. dd if=/dev/sdb1 bs=512 count=1 of=/windows/boot.lnx
2. I copied this file over to my windows c:\linux folder. 
3. I edited my boot.ini file by adding this to the last line
       c:\linux\boot.lnx="Ubuntu Linux (Grub)"

When I reboot the system, the windows loader shows my linux option. When I select the option, my pc just reboots. I keep selecting the Linux option but it just keeps rebooting. I select the windows options and windows boots up just fine. Any ideas why?

Oh, I did make the / partion on the linux drive bootable. Here's some more info if needed.  
sdb1   pri    8GB    /
sdb2   pri    50     /windows  (FAT32)
sdb5   log    12     swap
sdb6   log     8     /var
sdb7   log     5     /tmp
sdb8   log     20    /usr
sdb9   log    20     /opt
sdb10  log    50     /home

After setting up the above partions the ubuntu server installer completed the installation. It did as where to install grub and I took the default (sdb1,0)


thanks for all those that read and respond. It is very much appreciated.

thanks,
 Brent

---

### Post by belbakri on 2008-04-27
Hi, 
putting linux on my pc and dual booting is new to me so forgive me for my ignorance. I've installed ubunta 8.04 on a scocond hard drive with grub in the / dir (sd1,0). I'm trying to get the windows bootloader to boot linux. I've followed alot of the help on the net. Here's what I've done after installing Utunbu

1. dd if=/dev/sdb1 bs=512 count=1 of=/windows/boot.lnx
2. I copied this file over to my windows c:\linux folder. 
3. I edited my boot.ini file by adding this to the last line
c:\linux\boot.lnx="Ubuntu Linux (Grub)"

When I reboot the system, the windows loader shows my linux option. When I select the option, my pc just reboots. I keep selecting the Linux option but it just keeps rebooting. I select the windows options and windows boots up just fine. Any ideas why?

Oh, I did make the / partion on the linux drive bootable. Here's some more info if needed. 
sdb1 pri 8GB /
sdb2 pri 50 /windows (FAT32)
sdb5 log 12 swap
sdb6 log 8 /var
sdb7 log 5 /tmp
sdb8 log 20 /usr
sdb9 log 20 /opt
sdb10 log 50 /home

After setting up the above partions the ubuntu server installer completed the installation. It did ask where to install grub and I took the default (sdb1,0) and I verified that it's in the /boot/dir

I've looked at the menu.lst file and it looks good. It has :

default 0
title Utunbu 8.04....
root  (hd1,0)
kernel    /boot/....
initrd    /boot/...
quiet

title ....


thanks for all those that read and respond. It is very much appreciated.

thanks,
Brent

---

### Post by belbakri on 2008-04-27
I'm new to al of this and I could really use some help.  I've installed the 8.04 server on a second hard drive and I'm trying to use windows NTBL to load linux.   I've look on line found all the things I need to do, and I've done it.   ie

made  a bootable partion /boot on sencod hard drive in the first portion of the drive and had grub installed there.

I did the dd if=/dev/sdb1 bs=512 count=1 of=/osshare/boot.lnx

edited boot.ini to include boot.lnx as an option

Heres the problem:   
 Windows bootloader loads and I can see my linux option.
 I select the linux option, then the screen goes blank wtih
 the word GRUB at the top and that's it.

Any ideas?  Thanks,
 Brent

---

### Post by belbakri on 2008-04-27
I'm new to al of this and I could really use some help. I've installed the 8.04 server on a second hard drive and I'm trying to use windows NTBL to load linux. I've look on line found all the things I need to do, and I've done it. ie

made a bootable partion /boot on sencod hard drive in the first portion of the drive and had grub installed there.

I did the dd if=/dev/sdb1 bs=512 count=1 of=/osshare/boot.lnx

edited boot.ini to include boot.lnx as an option

Heres the problem: 
Windows bootloader loads and I can see my linux option.
I select the linux option, then the screen goes blank wtih
the word GRUB at the top and that's it.

Any ideas? Thanks,
Brent

---

