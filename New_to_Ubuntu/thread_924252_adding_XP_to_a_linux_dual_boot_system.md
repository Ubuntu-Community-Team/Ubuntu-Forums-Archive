---
title: "adding XP to a linux dual boot system"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-09-19
hi
I am currently dual booting ubuntu/ mint but wish to triple boot with a small XP partition too(for Word and games that I cannot get to run in Linux)
I have the cdroms for all three os
What is the best way to approach this process?
Thanks in advance

---

### Post by waspbr on 2008-09-19
if you isntall windows, it is going to write grub off and replace it with its own MBR.

you can either use a supergrub cd to reisntall it, or reinstall one of mint or ubuntu partitions, which would also install grub.


 my 23 cents

---

### Post by MarlonDean on 2008-09-19
I am not an expert on the matter, but Ubuntu has the best dectection of other operating systems (of the 3 mentioned), so I suggest you install Xp, then mint, and finally Ubuntu. Ubuntu will see the others and will set up GRUB with the choices

---

### Post by bumanie on 2008-09-19
As you already have mint/ubuntu installed things will be a little bit more difficult as windows prefers the first partition of the first hard drive. Need to know more information such as how many hard drives you have, present partitions etc as windows will not boot from within a logical partition. Post the output of > sudo fdisk - luSuspect you may have to shift some partitions around with gparted, install windows and then reinstall grub, but others may know of an easier way.

---

### Post by caljohnsmith on 2008-09-19
> **bumanie said:**
> As you already have mint/ubuntu installed things will be a little bit more difficult as windows prefers the first partition of the first hard drive. Need to know more information such as how many hard drives you have, present partitions etc as windows will not boot from within a logical partition. Post the output of Suspect you may have to shift some partitions around with gparted, install windows and then reinstall grub, but others may know of an easier way.
Actually, I believe that Windows will install to any primary partition without much trouble, and one of the forum members meierfra even figured out how to [boot Windows XP or Vista from a logical partiton]("http://ubuntuforums.org/showthread.php?t=813628"); but of course I certainly wouldn't recommend it if you can install Windows to a primary partition instead. :)

---

### Post by kansasnoob on 2008-09-19
Well, start by looking at this guide:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

What you'll want to pay special attention to is the repartitioning and then restoring grub.

If you'd post a screenshot of Gparted (aka:Partition Editor) I'd be willing to make some suggestions. If so also post the output of:

```
 sudo fdisk -l
```

NOTE: That's a lower case L, not a one!

I have Win XP, Hardy, and Mint Elyssa:

[ATTACH]85785[/ATTACH]

As far as restoring grub you just need to know your partition numbers and how grub's numbering system works:

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

Your actual numbers used to restore grub will be different than what the APC tutorial shows!

---

### Post by ibuclaw on 2008-09-19
Grub is easily restored if the MBR is overwritten.

After you've installed Windows and have gotten it setup. Insert your Ubuntu LiveCD and boot up into the Live Environment.

Once in, open a terminal and run grub
```
sudo grub
```
You will enter a grub prompt like so
```
grub>
```

First, find out which partition contains the boot information for grub.
```
find /boot/grub/stage1
```
Then set the root partition, the Linux installation with that boot directory in.
```
root (hd0,0)
```
With that done, tell grub to install in your primary MBR.
```
setup (hd0)
```
And you are done. Just quit and reboot.

Although, you will need to edit the /boot/grub/menu.lst file to include the Windows Installation afterwards.

Regards
Iain

---

### Post by caljohnsmith on 2008-09-19
> **tinivole said:**
> 
First, find out which partition contains the boot information for grub.
```
find /boot/grub/stage1
```
Then set the root partition, the Linux installation with that boot directory in.
```
root [COLOR="Blue"](hd0,0)[/COLOR]
```
With that done, tell grub to install in your primary MBR.
```
setup (hd0)
```
And you are done. Just quit and reboot.
I think the above needs maybe a small clarification, tinivole: if you run the Grub commands as you give them, it will reinstall Grub to the MBR and point it to (hd0,0), or sda1, for all its system files (menu.lst, etc). But we can't say for sure that the Linux partition is on sda1, so that is the purpose of that "find" command that you gave before doing the "root" and "setup" commands. :) The find command should tell you which partition has Grub's stage1 file, assuming that stage1 is in the /boot/grub directory of some partition; from that we assume that all of Grub's other files are in the same directory. Sometimes people have a /boot partition, and in that case the Grub files are actually located in /grub and not /boot/grub. So for that possibility, you would have to search using:
```
find /grub/stage1
```

---

### Post by abdulkrem on 2008-09-19
Hi guys...
I tried this way before and it worked with me but it give u the same list of OSs that u have before . so
is there any way to reinstall grub to add new OSs to the list
thank u very much

---

### Post by caljohnsmith on 2008-09-19
> **abdulkrem said:**
> Hi guys...
I tried this way before and it worked with me but it give u the same list of OSs that u have before . so
is there any way to reinstall grub to add new OSs to the list
thank u very much
If you want to add new OSes to your Grub menu, you have to modify your /boot/grub/menu.lst. If you need help with that, first post:
```
sudo fdisk -lu
```

---

