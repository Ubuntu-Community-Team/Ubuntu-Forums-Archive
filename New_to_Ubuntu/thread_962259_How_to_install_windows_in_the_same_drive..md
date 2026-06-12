---
title: "How to install windows in the same drive."
date: 2008-10-29
forum: New to Ubuntu
---

### Post by theamber on 2008-10-29
Hi, I have Hardy Heron installed I downloaded all the updates and all so I dont want to erase it. now I want to know if is possible to particion my hard drive and install windows XP so I can chose which one to boot from and how do I do that when Ubuntu is already installed, thanks.

---

### Post by Zalbor on 2008-10-29
That requires more work than installing windows first, but it's definitely possible. I've not done it myself, but I think the following should work:

First you'll need to make room for windows on your hard drive. You can use the Ubuntu CD (or another liveCD) to use gparted (System>Administration>Partition editor) and shrink your ubuntu partition(s). You have to do that from a liveCD because that way your drive won't be in use at the time.

Then install windows normally, but make sure to do it in a new partition in the unpartitioned space. After you're done, you'll only be able to boot windows and that's why you'll need the following step.

Follow the instructions here:
[https://help.ubuntu.com/community/GrubHowto#Command%20line](https://help.ubuntu.com/community/GrubHowto#Command%20line)
to restore grub.

Finally, you'll have to make an entry in your /boot/grub/menu.lst file so that grub will be able to load windows. I'd show you mine as an example, but I'm not at my home computer right now.

EDIT: Here's a relevant page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by theamber on 2008-10-29
When I installed Ubuntu I don't remember seeing any options like that. I downloaded the Hardy Heron 8.04 I am not sure if ti has the liveCD option. 
If I do that will that allow me to chose either operating system to boot from right after I turn on the machine?
Also how do I install Ubuntu in a Machine that has windows already and I want to leave the windows untouched, thanks.

---

### Post by ronocdh on 2008-10-29
Zalbor hit the nail on the head with his response. I think you should use the GParted CD, boot to that, then shrink your Ubuntu (ext3) partition and create one for Windows. Are you running WinXP? If so, I recommend FAT32. Reduced performance, perhaps, but easy read/write from Ubuntu.

After you create it and install Windows (be very careful to install Windows onto the proper partition! it likes to try to eat the whole drive in one fell swoop), you'll have to reinstall GRUB to repair the MBR that WinXP destroyed. Procedure for that is to boot to the Ubuntu live CD and use ```
sudo grub
``` Search forums for more help there....

---

### Post by kansasnoob on 2008-10-29
Here's a very simple guide:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

It works!

---

