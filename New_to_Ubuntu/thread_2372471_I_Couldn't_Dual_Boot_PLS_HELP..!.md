---
title: "I Couldn't Dual Boot PLS HELP..!"
date: 2017-09-25
forum: New to Ubuntu
---

### Post by leonic1 on 2017-09-25
[SIZE=1]Two days with i am busy on to dual booting my acer f-5 laptop. but I couldn't...
I  shrinked disc after that i installed ubuntu from usb device and[FONT=arial black] **[FONT=book antiqua]when i reboot always windows is opening[/FONT]**[/FONT], grub is inactive,I disabled secure boot,i tried easybcd ,i tried every commands in cmd,I tried every single video on Youtube but unfortunately nothing's changed.
I am trying to do windows 10 and ubuntu working in one laptop this is all that i want...Sorry for my bad english.
Pls Help me People[/SIZE]... :(

---

### Post by yancek on 2017-09-25
Ubuntu has an official documentation page for dual booting with windows 10 uefi, see the link below as it has all the information you will need.  If you don't understand something post back with a specific question.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-09-25
Please do not shout. We are here to help, but need to know what your issues are.

What brand/model system, and what video card/chip?

Is system newer UEFI or older BIOS? And did you install Ubuntu in same boot mode as Windows?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

EasyBCD is a Windows tool, not really required with newer UEFI systems unless used just to repair Windows BCD.

---

