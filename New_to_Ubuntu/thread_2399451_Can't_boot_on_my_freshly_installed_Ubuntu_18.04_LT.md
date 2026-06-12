---
title: "Can't boot on my freshly installed Ubuntu 18.04 LTS"
date: 2018-08-25
forum: New to Ubuntu
---

### Post by nfnfnfnf on 2018-08-25
Hi everyone
I'm having trouble installing Ubuntu on a different partition on my acer aspire V15 nitro black, that already has win 10 installed
Here's a screenshot of Gparted taken inside an Ubuntu Live session.> [IMG]https://image.noelshack.com/fichiers/2018/34/6/1535208331-xd.png[/IMG]
sda1, sda2 and sda3 are the partitions that were already existing, containing the EFI, windows 10 and my data. I created the sda5 (ext4 format) to install Ubuntu (which should already be in there). I have no clue what sd4 is.
Since I can't launch ubuntu at start using my efi bios, I'm guessing I just screwed by installing it without grub. What would be the easiest way to install grub without losing my datas or my previous OS? I'm starting to think I made enough mistakes today, that's why I'm here to seek advices :p

Thank you very much everyone :)

EDIT: oh yeah sorry screenshot is in french and I'm a terrible english speaker... Do not hesitate to tell me If what I'm saying is unclear to you guys :p

---

### Post by oldfred on 2018-08-25
There also is a French forum, not sure how active it is.

All Acer have a unique requirement of setting "trust" in UEFI to allow boot of the Ubuntu/grub .efi boot files.
Many Acer have needed UEFI updated from Acer also.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

