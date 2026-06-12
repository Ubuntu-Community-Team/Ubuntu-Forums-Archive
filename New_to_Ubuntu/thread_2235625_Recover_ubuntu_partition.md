---
title: "Recover ubuntu partition"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by suryaprakash498 on 2014-07-22
I have Dual boot in my laptop one is Windows 7 ultimate and another is ubuntu 14.04 LTS.
I have seperate partition for ubuntu & windows and with grub i am selecting the OS 
Now my Windows have a problem so i am reinstalling the OS of Windows in the partition of windows 
but if i reinstalled i will loose ubuntu for sure.....I dont want to loose ubuntu...
Is there any way i can install windows without loosing ubuntu?

:mad:

---

### Post by veddox on 2014-07-22
You should be able to install Windows into the correct partition without deleting Ubuntu. Just look carefully at the options it gives you during install, and you'll find the correct way to go.

However, you will need to [reinstall GRUB]("https://help.ubuntu.com/community/Grub2/Installing") afterwards, as Windows will reset the computer to its own bootloader. This shouldn't present too many difficulties though.

IMPORTANT: Whatever you do, don't forget to back up anyway. No matter how safe the proceedings look, things can always go wrong. So make sure you back up...

---

### Post by coffeecat on 2014-07-22
veddox is right to say that you can re-install Windows into the same partition without losing Ubuntu, and that the only thing you will need to do is to re-install GRUB afterwards. However, there are two big caveats.

1 - If you are re-installing from an OEM recovery partition or recovery media, you may only be able to restore your machine to its factory default state and everything will be overwritten on the hard drive. Some manufacturer&#8217;s recovery utilities are more flexible than others and do allow re-installation to a selected partition, but you need to check this if this is what you are doing. Your mention of Windows 7 Ultimate suggests you are not using an OEM recovery utility but a Microsoft installation disc, in which case you need to be aware of the following.

2 - If you are re-installing Windows from a Microsoft installation disc and if any of your Ubuntu partitions are the first logical partition, then in certain circumstances the Windows installer will simply delete that first logical partition without any warning. Often the first logical partition is your Ubuntu root partition, so that would be catastrophic. If you are intending to use a Microsoft installation disc, post this terminal output from Ubuntu:

```
sudo fdisk -l
mount
```

---

