---
title: "Dual Boot two distros"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by Richard_Sluder on 2014-09-29
I was successful at loading Ubuntu and Mint as a dual boot and they are both working. How do I remove one of them and keep my favorite?

---

### Post by Forbees on 2014-09-29
use a program like Gparted to delete the partition you don't want, then resize the partition you do want to take the whole drive.

depending on where Grub is at you might have to reinstall grub with a live disk

i bet there is an easier way, but this is what i've always done lol

---

### Post by nerdtron on 2014-09-29
Single hard drive dual boot right?
Which OS came first first Ubuntu or Mint?
Which do you want to remove?

---

### Post by Impavidus on 2014-09-29
Boot the system that you want to keep and reinstall grub to be sure grub is controlled by the system you want to keep. Then delete the partition of the system that you want to remove. Finally update grub.

---

### Post by Richard_Sluder on 2014-09-29
Thanks a lot. Will give that a try. Wanted to try Gparted anyway.

---

### Post by Vladlenin5000 on 2014-09-29
To make it clear - if not already - you want to install grub from within the OS you want to keep. Unless explicitly installed in a different way, the second installed OS is the one currently managing the grub.

---

### Post by Richard_Sluder on 2014-09-29
Right! Mint came first. Want to keep Ubuntu.

---

### Post by Vladlenin5000 on 2014-09-29
> **Richard_Sluder said:**
> Right! Mint came first. Want to keep Ubuntu.

So it *should* be safe to proceed with the previously recommended method. After that boot into Ubuntu and ```
sudo update-grub
``` in order to remove the now obsolete entry for Mint.

---

### Post by Impavidus on 2014-09-30
> **Vladlenin5000 said:**
> Unless explicitly installed in a different way, the second installed OS is the one currently managing the grub.
In general, yes, but there is one exception. If there is an update to grub itself, it may be reinstalled. This way the last system to install the update to grub can take control of grub. A few months ago there was an update to grub, causing my old 12.04 system to take back control from my new 14.04 system.

If Ubuntu is listed highest on the grub menu, Ubuntu should be the one controlling grub and it should be safe to delete Mint.

---

### Post by oldfred on 2014-09-30
Grub does remember where to reinstall. If you have multiple installs or drives you can uncheck all re-install locations and it will then not reinstall. Or set install location to a partition as a throw away. Normally installing to a partition is not recommended.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not normally choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

