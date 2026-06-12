---
title: "2 ubunts after update"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-05-30
i dual boot with xp, so i have grub. when i turn the computer on, i can choose to boot ubuntu, "safe mode" ubuntu, memtest, or xp. after one of the updates, i now have ubuntu (i think gnome version) 2.6.24-16 and 2.6.24-17 and same thing for safe mode. is this supposed to happen?

---

### Post by jaithehulk on 2008-05-30
I think those are two kernel version of the Same UBUNTU...
So there is nothing to worry about...even i hav the 2 kernels.

---

### Post by quelx on 2008-05-30
Yes it is a new kernel or core file for Ubuntu, the file manages the software/hardware layer, and -17 is an the updated version.  It's safe to have both and a good thing is something goes awry with the newer version.  Generally they are released to support new hardware or fix bugs.

---

### Post by wolfen69 on 2008-05-30
that's because you updated your kernel. you now have a choice between old and new. no big deal.

---

### Post by SunnyRabbiera on 2008-05-30
right, its nothing to worry about.

---

### Post by kansasnoob on 2008-05-30
Yes. That's the result of a kernel update.

I asked a question about hiding the older kernel and got many great answers here:

[http://ubuntuforums.org/showthread.php?t=808132](http://ubuntuforums.org/showthread.php?t=808132)

---

### Post by wannadumpwindows on 2008-05-30
Yes, that's perfectly normal. Each one with a different number is a different kernel. The get updated from time to time to add more hardware support, bug fixes and other updates. It doesn't hurt anything at all, and it's a good idea to at least keep one extra in case something ever goes wrong with an update, you have a working kernel to revert back to so you can try and figure out what's going on. But you can always edit the menu to only show the ones you want.

---

### Post by iaculallad on 2008-05-30
And you have the option of removing/deleting the old kernel and edit your GRUB menu list (to delete any traces of your old kernel) to display/boot only on the updated kernel.

---

### Post by bumanie on 2008-05-30
All you have is an upgraded kernel and the previous one too. It is OK to have more than one kernel to choose from, just in case an update doesn't suit your computer configuration - you can then revert to an older kernel that you know works. If you want a smaller list, you can > sudo gedit /boot/grub/menu.lst and in front of the older kernel entries place a # This will stop it from showing in the list, but it doesn't remove the kernel so you can uncomment and use it later if you need to.

---

### Post by jlandaw on 2008-05-30
Ubuntu updated the Kernel, and now you have two, of them. you can remove the the old one from the list by following this tutorual:

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")

---

### Post by mcduck on 2008-05-31
Instead of removing the old kernel from the Grub menu it's better to just uninstall it with Synaptic/apt-get after you have confirmed that the new kernel works fine.

If you just remove the old kernel from the menu, it will still be on your hard drive wasting disk space, and when it's not even in the menu you'd have pretty hard time trying to use it.. (well, having one extra kernel doesn't take _that_ much space, but sooner or later you'll get more of them and the amount of wasted space will increase..)

So just open Synaptic, search for "linux" in package name to find the kernel packages and uninstall the old version: It will be automatically removed from the Grub menu as well.

(the packages you are looking for are "linux-image", "linux-headers" and "linux-restricted-modules" if I remember the names right..)

---

