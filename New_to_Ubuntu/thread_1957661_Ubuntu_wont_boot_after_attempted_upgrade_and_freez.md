---
title: "Ubuntu wont boot after attempted upgrade and freeze"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by krisa87 on 2012-04-12
Hi Everyone,

Last night I was upgrading Ubuntu as I was still using the 10.04 version.
While updating (about halfway) to 10.10, my laptop froze and I had to force a shut down.
When I tried to reboot, ubuntu wouldnt start up and I was left in the command prompt with the following message:

Gave up waiting for root device. Common problems:
- Bott args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; Is /dev)

ALERT! /dev/disk/by-uuid/44aa0716-ec-4fd1-97e4-6229b178574c does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11_ built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)



PLEASE HELP ANYONE!!! I am without a computer and have no idea what to do.

Thanks

---

### Post by ixtok on 2012-04-13
I am just a novice and since none of the experts have answered you, what I would do is get a live cd or usb of whatever version Ubuntu you want, run it as live, back up any of your essential files/data externally and then do a fresh install.

---

### Post by Michael Dooley on 2012-04-13
Please use some google-foo. For your search term, I'd use the following:

ubuntuforums: initramfs

Good luck krisa87. Please let us know how your problem is going - whether it is on its way to being solved or not.

---

### Post by NikTh on 2012-04-13
Hi ,
Do you really want the 10.10 version.. ? this version expired 2-3 days ago. 
I suggest to download an iso of 11.04 and after ... Then burn it and install from beginning. Probably you will lose your data , but if you want to backup do it with the existing (i guess) iso of 10.10 .

---

### Post by pierreyy on 2012-04-13
I would suggest a live cd/usb to recover and backup your files, after that a re-install of the OS.

---

### Post by daslinkard on 2012-04-13
It seems that someone else had this exact issue as you....and [this is how they fixed it]("http://ubuntuforums.org/showpost.php?p=6581939&postcount=322").  Hope this helps.

Or you can try this [link]("http://ubuntuforums.org/showthread.php?t=1018403&page=2") in which I found the above link.

---

### Post by jlownie on 2012-07-20
I had the same problem, and the way I fixed it was to edit the entries in /boot/grub/menu.lst and change root=<uuid> to root=/dev/sda1.  Also I added rootdelay=90.  

You can do this from the startup grub menu, something like pressing 'e' when selecting a menu item?

Hope this helps someone.

- James

---

### Post by YannBuntu on 2012-07-21
A broken upgrade generally breaks many system functions.
The easiest and fastest solution to repair the system files is to burn a UbuntuCD and follow this tutorial: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

Remark: 10.10 is obsolete. Use a 10.04 or 12.04 CD.

---

