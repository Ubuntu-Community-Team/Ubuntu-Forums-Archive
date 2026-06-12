---
title: "Grub is missing, cannot open windows OS"
date: 2018-04-28
forum: New to Ubuntu
---

### Post by gamseb on 2018-04-28
I have installed a dual boot of Ubuntu 18.04 LTS on my Acer Aspire V 15 computer. The other operating system is windows 10. After installation there is no grub and I cannot access the windows OS. 
Any help would be greatly appreciated.

---

### Post by kagashe on 2018-04-28
There must be some way to open Boot Menu or BIOS on your machine. On Boot Menu select Windows or on BIOS change the boot order to bring Windows on top, save and reboot.

This may help:
[https://ame.answers.acer.com/app/answers/detail/a_id/7550/~/changing-boot-order]("https://ame.answers.acer.com/app/answers/detail/a_id/7550/~/changing-boot-order")

It seems Grub is broken. You can boot into Live CD or USB, install Boot Repair and try restoring Grub Menu entries.

Kamalakar

---

### Post by yancek on 2018-04-28
If windows 10 was pre-installed, it was almost certainly using UEFI so you would need to install Ubuntu UEFI.  There are a number of possible problems.  Can you boot Ubuntu?  If not use the Ubuntu install DVD/flash drive and select the option to try ubuntu and when you get to the Desktop, open a web browser and go to the link below and download and run boot repair selecting the option in boot repair to Create BootInfo Summary.  It will give you a link which you can post here so that members can review the output and make suggestions.  Select the 2nd option to use the ppa to get boot repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You might also review the Ubuntu documentation on dual booting with windows 10 at the link below and see if it compares to what you actually did. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by gamseb on 2018-04-28
Yes, I am suing a laptop with a preinstalled windows 10. I am using ubuntu as I cannot enter windows, sadly I am pretty sure it is not UEFI. I have tried to use boot-repait, sadly it did not work. :/ Any way I can change my Ubuntu to the UEFI version?

---

### Post by yancek on 2018-04-28
If you can use Ubuntu, the answers to your questions are at the site I posted above, second link.  There's a command to run to tell if it is UEFI and it also explains how to change to GPT.  What didn't work about boot repair?  Were you unable to select the Create BootInfo Summary option, did it not run?  The install DVD/flash drive should be able to boot UEFI or Legacy, you need your BIOS set correctly.  Not much point in making suggestions until you post the boot repair output.

---

