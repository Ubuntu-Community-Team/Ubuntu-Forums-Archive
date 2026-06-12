---
title: "Ubuntu 12.10 / Windows 8 Dual Boot UEFI"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by rL1rj19Ko2 on 2013-04-18
Hello all, I used to have Ubuntu 12.10 x64 installed and dual booting with PRE-INSTALLED Windows 8 on my laptop with UEFI. Now I want to do it again, however, there is something that I just can't seem to find an answer to..  I want to know if anybody can tell me how I can put Ubuntu 12.10 into the Windows 8 boot loader so that the computer boots into the Windows 8 OS selection screen? I've found one or two articles on how to do this before, one is [http://askubuntu.com/questions/230878/dual-boot-windows-8-and-ubuntu-with-windows-8-boot-manager](http://askubuntu.com/questions/230878/dual-boot-windows-8-and-ubuntu-with-windows-8-boot-manager) but it clearly states in the article that this probably will not work with Windows 8 PRE-INSTALLED. So is there just no way to do it at all? I'm going to reinstall either way, but I'd really like to make it happen this way instead of the purple GRUB2 boot screen. Please let me know if there's any way to create a Ubuntu 12.10 entry in the Windows 8 boot loader (pre-installed :))! Thanks in advance.

---

### Post by oldfred on 2013-04-19
I know nothing about EasyBCD. For a while they did not have a version that worked with UEFI.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

    
This suggests EasyBCD.
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

If you like pretty, more like a Mac:
 Alternative efi boot Manager for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
 More info on secure boot - Ubuntu's shim may need changing to work with Refind
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)



        Dell 14z used Dell Recovery and Refind Boot Manager
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)

---

### Post by jjhiza on 2013-04-19
Not to dissuade you in your attempts, but I've only ever run into issues, trying to dual boot in UEFI mode. I've found it much easier to have two completely separate systems - Windows 8 in Secure/UEFI mode, and Ubuntu in Insecure/CSM mode. I've never had any issues doing things that way, and my machine runs perfectly fine; I just have to take a few extra seconds in BIOS, if I want to switch from one to the other. If this is the way you're currently running your setup, I'd suggest just sticking with it - especially in light of the issues some people seem to be having with UEFI installs on 13.04 (if you plan on updating).

---

