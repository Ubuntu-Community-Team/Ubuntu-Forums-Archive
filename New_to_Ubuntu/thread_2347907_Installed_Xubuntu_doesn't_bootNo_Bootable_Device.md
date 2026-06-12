---
title: "Installed Xubuntu doesn't boot/No Bootable Device"
date: 2016-12-29
forum: New to Ubuntu
---

### Post by daichin2 on 2016-12-29
I've just built a 500GB ssd into my Acer Aspire F15 having had a 1TB hdd installed before.Now having installed first Ubuntu in several different versions, while cleaning the Partitions using Gparted between each new try, I asked a friend who adviced my to try xubuntu since it worked better for him and he told me to try Bootrepair, and so did I( the log thingy is at: [http://paste.ubuntu.com/23708203/](http://paste.ubuntu.com/23708203/))
Yet having tried several more or less useful advices from an aweful huge amount of other threads and forums the System doesn't boot.
Thanks a lot in advance for any help
P.s: sry for probable Mistakes in language or the thread starting itself im neither native speaker nor used to writing in forums

---

### Post by oldfred on 2016-12-31
Did you install in UEFI boot mode?
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Acer in UEFI boot mode has a unique requirement to set a supervisory password in UEFI and then from UEFI enable "trust" on the ubuntu/grub .efi boot files.
Also some threads mention down grading UEFI from Acer. But newer threads say newest UEFI from Acer works. So make sure you have newest UEFI from Acer.

       
 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
    
       
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

