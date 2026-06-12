---
title: "No Boot Device Found"
date: 2018-03-06
forum: New to Ubuntu
---

### Post by Drowz0r on 2018-03-06
Hello all

I'm trying to install Lubuntu (latest version) on an Acer Aspire ES 11 (ES1-132-C974) with an eMMC of 32GB

The installer and everything ran without issue - but upon removing the DVD when prompted and rebooting, I get the error "no boot device found" with a picture of a HDD on the screen.

I've found a bunch of threads talking about similar issues and most seemingly to do with acer, but I've not been able to fix this yet.

Some said you need to disable secure boot, which I managed to do by setting a supervisior password and then disabling the secure boot but that didn't get me anywhere closer. I've tried changing the boot order of devices, HDD1 and the EMMC devices I've swapped around, using secure or not secure booting with no success.

I don't suppose anyone has an answer? Some said about changing the EFI settings or something in the bios, but my bios has no such settings.

Any help would be appreciated...

---

### Post by oldfred on 2018-03-06
Acer has a unique requirement of setting "trust" on the UEFI boot files.
But some models seem to have issues getting to those UEFI menu settings.
Make sure you have newest UEFI from Acer.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

Some do need other work arounds.
       
 Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269)
[https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533](https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533)

---

### Post by Drowz0r on 2018-03-06
Hey @oldfred

Thanks for your reply, maybe I wasn't clear but I cannot select any options for UEFI. They simply aren't in the bios. They seem to usually sit in the security tab but even after entering a supervisor password and disabling secure boot, they do not appear.

The bottom threads I'll try but honestly it seems a bit much for me to understand and I'm not sure they apply :(

---

### Post by oldfred on 2018-03-06
That is/was a problem with some versions of Acer's UEFI, that is why you probably need the newest UEFI from Acer.
Several more with similar issue, so not sure if Acer regressed and UEFI does not have option, or if you have old UEFI?

[https://ubuntuforums.org/showthread.php?t=2384706](https://ubuntuforums.org/showthread.php?t=2384706)

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer ES1-331 laptops Strange differences at new installations
[https://ubuntuforums.org/showthread.php?t=2362511](https://ubuntuforums.org/showthread.php?t=2362511)

Just to confirm your install is correct.
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Drowz0r on 2018-03-07
Man Acer don't make it easy...

Thanks. I'm still fiddling around with it - I've noticed they've actually sent me the 1.1ghz model instead of the 2.00ghz I actually ordered, so I need to return this one... but at least I should be able to get the new one up and running reasonably quickly. I'll let you know how it goes.

Thanks again!

---

### Post by volaer2 on 2018-11-11
I have Acer ES1-132 netbook. Same here, I can't boot after install and it says no bootable device. I tried working in the bios but there's no UEFI option at all. I even played with the admin password, still no use. I can't find a step by step instructions on how to resolve this. There's one thread that says rEFInd boot loader into /boot/efi/EFI/Microsoft/Boot resolved his problem but did not say the step by step process. Also, my netbook did not come with Windows. It came with Endless OS which run very slow in it. So I decided to install Ubuntu instead, only to my disappointment that I still can't find a solution for it to boot. Really appreciate if someone can give me a good step step solution that I can follow.

---

### Post by oldfred on 2018-11-11
The several links in post #2 all seem to give same instructions and that is from users with Acer.

Have you updated UEFI from Acer. Many older systems had to have update to have available settings when Secure Boot was turned on. Early fix was to downgrade to older UEFI as sometimes that  worked. But many newer posts say newest UEFI works.
       [https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing](https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing) 
            Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431) 
            Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer ES1-331 laptops Strange differences at new installations
[https://ubuntuforums.org/showthread.php?t=2362511](https://ubuntuforums.org/showthread.php?t=2362511) 
            Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594) 
    
       Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    
Some more:

---

