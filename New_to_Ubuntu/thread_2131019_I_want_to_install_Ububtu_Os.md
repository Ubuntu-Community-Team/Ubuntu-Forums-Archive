---
title: "I want to install Ububtu Os?"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by manigopal on 2013-03-31
**I want to install Ububtu Os?**

                   But my friends say that if you  install linux os and if tried to install the windows all your datas will  be erased and datas will be lost ?  pals help
                                    **Additional Details**

                                     i  have nt asked for the dual boot option am asking if i install linux on  already a windows os installed PC and if suppose i want to reinstall my  windows can i do it?

---

### Post by coldcritter64 on 2013-03-31
Some community documentation for you to have a read of, for dual booting. Cheers

 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Edit: the link also covers, with further linking, installing Windows after Ubuntu, it is easy to fix the bootloader if overwritten by Windows from an Ubuntu live cd.

---

### Post by sammiev on 2013-03-31
Dual booting is easy to do on most computers but always make a system backup of the HD first.

---

### Post by coldraven on 2013-03-31
Installing Ubuntu is pretty easy but if you don't what you are doing you should copy all your data first.
If your data is important to you you should be making a backup copy anyway, hard drives do fail for various reasons.
Buy an external drive, they are not expensive.
Also you should make Windows restore discs you might need to re-install Windows at some time in the future.

---

### Post by grahammechanical on 2013-03-31
> [COLOR=#000000]i have nt asked for the dual boot option am asking if i install linux on already a windows os installed PC and if suppose i want to reinstall my windows can i do it?[/COLOR]

I am not sure I understand your question. But if we install another operating system _over_ an existing operating system, then the original operating system gets removed - deleted. If the hard disk or partition is formatted at the same time then all data will be lost. This will happen no matter the operating system that you are installing. For instance, install Windows 8 over Windows 7 and you loose Windows 7. If you have Windows install disks or some other means of re-installing then you can re-install Windows.

So, to re-install Windows you need Windows disks that will allow you to re-install. Do you have them?

When we install Ubuntu get get options. See image 4 in this link to Ubuntu installation intructions

[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

a) Use the entire disk. If we choose that then any data on the disk will be erased/deleted. This will include the existing operating system and all other files.

b) Install alongside. This will put Ubuntu on its own partition on the disk and not remove the other operating system. At boot time you will get a menu with the option to load Windows or Ubuntu.

c) Do something else. This is where we create partitions and tell Ubuntu which partition to install into. This will also give you a boot menu.

All of these choices require us to make careful preparation to avoid things going wrong.

Please note, we often have people say that they want to remove Windows and they go ahead and remove the Windows operating system. Then later they ask on this forum how to get Windows back. This is why many of us recommend that you dual boot. People change their minds and it is then too late to put things back.

Regards.

---

### Post by MaxLinuxLover on 2013-03-31
Just backup your data and get ubuntu. Once you go there, you will not want to go back to windows.

---

### Post by SuaSwe on 2013-03-31
I would recommend backing up all your data then shrinking your Windows partition [perhaps following this guide, if you're using Windows 7]("http://www.makeuseof.com/tag/shrink-extend-volumes-partitions-windows-7/") - you can then install Ubuntu in the newly available space. Always ensure that Windows is installed before Ubuntu, as Windows will not recognise a Linux partition (at least it never used to back in the day when I dual-booted).

---

### Post by Mark Phelps on 2013-03-31
As already mentioned, if you install any new OS over an existing OS, you will erase the existing OS -- regardless of which one you install first.

So, if you have already installed Ubuntu over the top of Windows, and you now want Windows back, you're out of luck -- you erased it when you installed Ubuntu.

---

