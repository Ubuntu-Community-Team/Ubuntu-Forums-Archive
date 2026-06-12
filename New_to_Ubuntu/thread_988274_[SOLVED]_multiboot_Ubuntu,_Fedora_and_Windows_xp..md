---
title: "[SOLVED] multiboot: Ubuntu, Fedora and Windows xp."
date: 2008-11-20
forum: New to Ubuntu
---

### Post by melrokz on 2008-11-20
Fedora's bootloader is grub, but I'm surprised that it does not support Ubuntu, while it can load xp. Moreover, I'd like to know how to install grub from the ubuntu live cd. Please reply soon.

---

### Post by markjensen on 2008-11-20
GRUB can support both.    What Fedora's installer does not check for, however, are existing other Linux installs.

I don't know of any Linux distro (there probably are some, I am just unaware of them) that modify grub's menu.lst for other distros.

Get a copy of your menu.lst (electronic "cp" is best, but you can just print it, too, if you need to) and when you install your additional Linux distro, you just need to make sure you add in all the various boot sections for your multi-boot yourself.

Of course, when you do install another distro, you take it upon yourself to not stomp all over another OSes partitions - that is, don't re-create a new /boot, or you lose whatever was in there.

With some specifics from you, like your current partitioning and current grub menu.lst file, we can offer specific advice for you. :)

---

### Post by caljohnsmith on 2008-11-20
So do you want Ubuntu or Fedora to be in charge of Grub at booting time, or doesn't it matter? Since it sounds like Fedora is all ready controlling Grub in the MBR (Master Boot Record), you could simply add the following entry to Fedora's menu.lst for Ubuntu:
```
title Ubuntu Grub Menu
configfile (hdX,Y)/boot/grub/menu.lst
```
Where (hdX,Y) is Ubuntu's partition (assuming you don't have a /boot partition). If you would like more specifics, how about posting:
```
sudo fdisk -lu
```
And please identify your partitions.

---

### Post by bodhi.zazen on 2008-11-20
Actually *most* distros will updae grub , Fedora, in general, is the "Odd man out".

The one issue you need to be aware of, by Default Fedora uses LVM, which means a separate /boot partition.

See this thread for some community tips on multi booting, there are several nice options.

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

