---
title: "[SOLVED] How can I reboot Kubuntu?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by roscal on 2008-06-08
I was having problems with my other machine yesterday.
It is dual boot with ntfs/XP on one partition, and ext3/Kubuntu on a second partition.

XP kept crashing (it's my wifes machine, she uses XP) and Grub would not always appear on rebooting, so I did a fixmbr with an XP disc, took the case off and gave it a good cleaning (I think it was just overheating actually).

Now I have no Grub anymore. Any hints on how I can reboot into Kubuntu again? It's still there obviously. Should I just reinstall Kubuntu again on the second partition, or is there an easier way?

Thanks folks!

---

### Post by Rocket2DMn on 2008-06-08
You can use the Super GRUB Disk to reinstall GRUB - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Or you can look at some other directions here to restore GRUB to the MBR - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by roscal on 2008-06-08
My goodness, that was fast, thank you!
It appears the super grub disc method will be the most appropriate and easiest for me. I actually have it somewhere on a cd here, but have never used it.
Thanks, that link is great.

---

### Post by ajgreeny on 2008-06-08
If you can't find the supergrub disk you can also do it with the kubuntu live CD as follows.

Boot into the kubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot kubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

---

