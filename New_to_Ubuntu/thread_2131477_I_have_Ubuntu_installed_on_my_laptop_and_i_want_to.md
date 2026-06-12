---
title: "I have Ubuntu installed on my laptop and i want to install windows7"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by Harvysideburns on 2013-04-01
I have Ubuntu installed on my laptop and i want to install windows7 and  make it dual booting. But i have no idea how to create partitions with  ubuntu that will allow me to install windows.

---

### Post by layers on 2013-04-01
Your general steps:


[LIST]
[*]Make space for Windows 7
[*]Install Windows 7
[*]Reinstate grub
[LIST]
[*]Mount the /boot partition
[*]Install the bootloader
[/LIST]
[/LIST]


Use gparted to make space for win7. Then install win7 on the partition you made. Then,
the whole 3rd step can be done with a simple program I think (boot-repair from live media). I have no idea how much you know, so ask first what you don't understand, because if you mess up any of these 3 steps, you risk loosing data.

---

### Post by claracc on 2013-04-02
Here, you have a step by step guide [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) to dual boot ubuntu/win 7. Note, point 6.

---

