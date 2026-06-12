---
title: "Need to install ubuntu on UEFI laptop"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by please_click_this on 2014-02-22
I have a cheap $300 Acer E1 series laptop with UEFI and Window$ 8. Btw, the only "BIOS" in the boot menu is UEFI. I want to wipe windows 8 COMPLETELY off the hdd and replace it with Ubuntu or Fedora. I'll try Ubuntu first even though I heard that Fedora has better support for all that UEFI junk. I wrote the 64 bit ubuntu ISO to USB (made with unetbootin) and DVD so that I could install it on my laptop.

First, I disabled that UEFI cr@p that billy put in my way. When I boot with a live USB or DVD of Ubuntu, I get a black screen with 3 options - Install, Try, Check something. When I choose install, I get a black screen. It stays there forever. How do I even know that I can install ubuntu on this system ? If its possible, please tell me the steps. I got this laptop for Linux only. 

Please help me.

---

### Post by Vladlenin5000 on 2014-02-22
Hi, welcome.
A comment and a suggestion followed by a question:
Regarding UEFI and considering you intend to have the Linux OS (Ubuntu) has the only OS in that machine you don't have to worry about UEFI. Ubuntu will install and work with or without it ("legacy" or whatever...). More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I would strongly suggest you select the "Try..." option before anything else and assure everything works in that live session. Then you can as well run the installer in that live session.
Although your idea is commendable - having a decent OS instead of the one forced by the manufacturer - I would advise caution. A quick Google search seems to indicate your notebook comes with a Broadcom WiFi card and that's a potential problem. The symptom you mentioned is unrelated but not a good sign either.
Now the question: What graphics chip it has (GPU)? The symptom you described has been reported with some nvidia cards. However, the same quick Google search apparently shows it has a standard integrated Intel HD graphics and those usually work fine out of the box and don't require additional drivers. It's possible to have many variants within the same "series", including the same model with an additional discrete nVIDIA (or ATI) card but for the price that's highly unlikely. 

Hopefully someone else here will be able to suggest a proper troubleshooting. Meanwhile, again, I suggest you to try in a live session and if it works check the WiFi. It's not a problem if it's not recognized, it should be fixable later with the system fully installed, it just requires an extra effort.

---

### Post by oldfred on 2014-02-22
Often better to use UEFI not BIOS. But you may install in  BIOS boot mode on a gpt drive, but can only dual boot from UEFI/BIOS menu not from grub.
Best to be sure that you can do everything you want from Ubuntu before deleting Windows. We get many who convert 100% to Ubuntu then come back and want to reinstall Windows for one game or application.
Best then to have full back up of Windows.
One user posted he just removed the Windows hard drive which is not even booted once and installs a new SSD. Then Ubuntu is very fast and he can later sell system with "new" Windows on hard drive.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

What cpu and video chip/card do you have. That can make a lot of difference. You may need nomodeset or other boot parameter depending on which video chip you have.

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

