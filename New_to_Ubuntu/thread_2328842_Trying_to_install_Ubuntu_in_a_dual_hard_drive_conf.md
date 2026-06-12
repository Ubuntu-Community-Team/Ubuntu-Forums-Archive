---
title: "Trying to install Ubuntu in a dual hard drive config"
date: 2016-06-24
forum: New to Ubuntu
---

### Post by Supratikn on 2016-06-24
Hello everyone!

I have a laptop(Lenovo Thinkpad T420) with a 130 gig ssd that has windows 10 and on it. I purchased a 480 gb ssd solely for ubuntu. Since I have a optical drive in my laptop, I purchased a caddy and put the ssd in it. Thus, I had a dual hard drive config. I created a Ubuntu 16.04 bootable usb by using Rufus. I initially tried to install Ubuntu by taking out my 130 gig ssd and installing Ubuntu on the 480 gb. However, when I restarted the computer, the laptop wouldn't boot from the Ubuntu ssd. After that, I tried installing by clicking "Something Else" during the installation and manually making partitions. Even that didn't work. The computer just wouldn't boot from the 480 gig ssd. I even went to the laptop's BIOS and changed the boot priority order. But it still wouldn't boot Ubuntu. Please help!

---

### Post by oldfred on 2016-06-24
Some systems will not boot from a DVD/CD caddy. Do you know for sure it does?
And if UEFI system, grub only installs to ESP - efi system partition on drive seen as sda. If caddy is seen as external drive then it can only boot from /EFI/Boot/bootx64.efi like the installer.

 The thermal updates were submitted today for the Linux 4.6 kernel merge window and there's a very important fix for at least some newer Lenovo laptops.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates)
Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170) 
      
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715) 
           
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)

---

