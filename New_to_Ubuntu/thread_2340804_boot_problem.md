---
title: "boot problem"
date: 2016-10-22
forum: New to Ubuntu
---

### Post by sultan1684 on 2016-10-22
Namste , people 
yesterday . i asked this question . [https://ubuntuforums.org/showthread.php?t=2340699](https://ubuntuforums.org/showthread.php?t=2340699)
every thing seems working fine . than i got notification of window 10 update . i updated window but now . i don't get boot option for [U]Uubuntu 16.04  
[/U]can any one tell me what is wrong with my system 
i have Acer Aspire E 11 notebook . 
intel celeron processor N2840 
intel graphics 
2GB DDR3 Memory 
500 GB HDD
and this is my boot info summary. 
 [http://paste2.org/PsYBbE5J](http://paste2.org/PsYBbE5J)
please halp me (sorry for bad English )

---

### Post by OctaVive on 2016-10-22
You have to reconfigure the GRUB bootloader. Sometimes, Windows 10 overrides the bootloader, which is quite annoying.

---

### Post by sultan1684 on 2016-10-22
how to do that

---

### Post by oldfred on 2016-10-22
As Boot-Repair suggests, you may want to turn Secure Boot off.
Windows on updates may reset system to have it first in UEFI boot order. So keep Ubuntu installer/Boot-Repair handy.

Did you set Supervisory password & trust on Ubuntu/grub .efi files?
Also do you have newest UEFI from Acer? Some older threads mention downgrading to older, but then even newer threads say newest UEFI from Acer fixes all issues.
       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
      
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    
You show a lot of Boot-Repair histories in efi partition sda2. You may want to clean out all but last one.

---

### Post by sultan1684 on 2016-10-22
thank you very much Oldfred . your suggestion solved my nightmares . you saved me 
thank you again

---

