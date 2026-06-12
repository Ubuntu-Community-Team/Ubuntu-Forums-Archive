---
title: "Newbie uefi secure mode"
date: 2017-12-14
forum: New to Ubuntu
---

### Post by tryme66 on 2017-12-14
So here I am, I completly deleted Windows of my PC & install Ubuntu 16.04. Damn I love for now, still just 2 days I have it. So I have problems to download apps with Ubuntu, So I disabled UEFI secure boot, now all is working, my question is: Is it safe to run Linux without UEFI Secure boot & do we have any softwares to download & protect my pc. I am a NEWBIE right now but planning to learn more about it.

Thank you, all others information is welcome. ):P

---

### Post by ajgreeny on 2017-12-14
Hi tryme66 and welcome to the forum.

Secure boot has absolutely nothing to do with Ubuntu and is most definitely not required to run any Linux distro as far as I'm aware, in fact I believe disabling secure boot removes a number of potential problems when installing proprietary drivers that need to access the kernel to add driver modules.

It is a system that was devised by Microsoft, as far as I'm aware, as part of the UEFI firmware that allows the computer to boot only systems that have been signed as secure by their makers.

Some Linux distros, including Ubuntu, have a signed kernel system that will work in a secure boot setup, but it adds nothing of real value to the running of the computer and I suspect the large majority of Linux users disable it.

Regarding your query "do we have any softwares to download & protect my pc?" I suggest you look carefully at the security pages for  Ubuntu which will tell you all you need to know.
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by oldfred on 2017-12-14
Ok, Suppose I am in marketing for Microsoft and every article published is about virus' with Windows. What better way to improve perception than to change to use "Secure Boot" as my default install. Even though it has nothing to do with 99% of the virus' out there, as they are not boot virus.
In fact the most famous BIOS boot virus was from Sony who wanted to make sure you were not playing any music.

Eventually we may want to turn on UEFI Secure Boot, but not really required now.

       Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by yancek on 2017-12-14
It's more about control by microsoft and does not do anything to make a system more secure, certainly not any Linux or non-windows OS.  The UEFI standards have been in development for well over a decade and Secure Boot is about the only thing microsoft contributed and in fact, is pretty useless.i

---

