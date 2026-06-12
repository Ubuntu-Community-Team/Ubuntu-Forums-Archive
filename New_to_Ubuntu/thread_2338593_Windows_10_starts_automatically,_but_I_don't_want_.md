---
title: "Windows 10 starts automatically, but I don't want it to"
date: 2016-09-29
forum: New to Ubuntu
---

### Post by daniel74z on 2016-09-29
I've installed Ubuntu 16 alongside an existing Windows 10 installation. No errors during install but, at boot, Windows starts and gives me no option to choose an OS to boot.

In Windows, I have disabled fast start, secure boot and hibernate. 

Running Ubuntu from my usb stick, I attempted to run boot-repair but it gave an error and the following link: [http://paste2.org/K5wE2pb7](http://paste2.org/K5wE2pb7)

Thanks for your thoughts and help.

---

### Post by oldfred on 2016-09-29
I see mention of Acer.
Did you set the supervisory password in UEFI and enable trust on the .efi boot files.
All Acer seem to require that.
Also make sure you have newest UEFI from Acer. Some older threads mention downgrading to an older UEFI, but then newer threads say Acer fixed issue and newest UEFI works.

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
            Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
            Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Secure settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

