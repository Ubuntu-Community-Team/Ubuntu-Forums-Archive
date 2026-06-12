---
title: "newbie dual boot from Acer Aspire E 15 E5-575-33BM ?"
date: 2017-12-27
forum: New to Ubuntu
---

### Post by joyful2 on 2017-12-27
Hello, 

The Acer Aspire E 15 E5-575-33BM is recommended in some online article as a great choice to dual boot Windows and Linux. 

Before I spend my money on the laptop, I'd like to verify that is true. The author of the article(s) doesn't appear to be reachable. 

This is the Acer page about it: [https://www.acer.com/ac/en/US/content/model/NX.GG5AA.005](https://www.acer.com/ac/en/US/content/model/NX.GG5AA.005)

When I used Ubuntu some years ago, I liked Xubuntu / XFCE. My "talents" are limited, but I can usually follow directions for installing etc. I had hoped I could download the installer, and simply follow prompts to make the new laptop dual boot (Win / XUBUNTU). Will there be anything else I'd need to do that the installer won't do for me? 

When I googled for information, I found old posts from 2015 and 2016 with folks complaining Ubuntu and other Linux distros would not install on this particular laptop. Hence my desire to make sure I don't screw up in my purchase. The price point and features of this laptop will suit my needs if it can be a dual boot machine. 

Thank you for any help. 
LM

---

### Post by oldfred on 2017-12-27
Do not install 17.10 for now. Issues with UEFI/BIOS, kernel & Intel driver that may not even be used.

       Acer Aspire ES (15 ES1-523-844Y)  works with some settings
[https://ubuntuforums.org/showthread.php?t=2364018](https://ubuntuforums.org/showthread.php?t=2364018)

For general UEFI install info see link in my signature below.

Acer does have a unique requirement of once installed, you have to set an UEFI password and enable "trust" on the .efi boot files.
Make sure you have newest UEFI from Acer. Some older threads mention downgrading UEFI, but newer one say the newer UEFI works.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[URL="http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742"]http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742
[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
[https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074](https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062) 
    
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by jeremy31 on 2017-12-27
I would also not recommend using a kernel from 4.11 to 4.13 as those are the ones where the issues exist with some InsydeH2O UEFI

---

### Post by joyful2 on 2017-12-27
Thank you OldFred and Jeremy for helping. All the links will take me some time to look through - but I'm glad to have the info! Hopefully I can grasp everything in there. 

> I would also not recommend using a kernel from 4.11 to 4.13

Is there a guide to which releases contain those kernels? 

Likely will have more questions after I wade through the reading. :-)  Thank you again. This is sounding hopeful.

---

