---
title: "Uninstall double install of Ubuntu"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by KatyG on 2013-02-02
I used a USB I made with Yummy to install Ubuntu on a PC that had no OS. I installed it once and then the USB was still attached  and a window came up saying an OS was detected and would I like to install it anyway, and I guess I clicked on the wrong thing and it installed it again and I couldn't figure out how to make it stop.

The USB partitioned my drive and now Ubuntu is on my laptop twice.

The LTS version I installed first is what I have been using, and it seems to run okay except some icons do not appear graphically along the left side. They are there, I can click on them and and if I hover over them the name appears, but they are invisible. It works okay, this just bugs me.

Three questions:
How can I get the extra Ubuntu off my computer?
How can I fix the icon problems I am having? Should I re-install?
Should I remove the partition in my hard drive if I don't need to run more than one OS on my computer?

I'll be researching this myself, but I would really appreciate advice from experienced users and computer people. Thanks.

---

### Post by Paqman on 2013-02-02
> **KatyG said:**
> 
How can I get the extra Ubuntu off my computer?


[LIST=1]
[*]Boot up into your USB stick.
[*]Open the Partition Editor
[*]Right click on your swap partition and "swapoff"
[*]Delete the partition containing the copy of Ubuntu you don't want
[*]If you want, expand the other Ubuntu partition into the space crated.
[/LIST]
This removes the Ubuntu install from your hard drive, but the entry for it in the bootloader remains. To deal with that boot into Ubuntu, open a terminal by hitting Ctrl-Alt-T and enter this command:
```
sudo update-grub
```
This will remove the other version of Ubuntu from the bootloader and it'll be like it never existed.

---

