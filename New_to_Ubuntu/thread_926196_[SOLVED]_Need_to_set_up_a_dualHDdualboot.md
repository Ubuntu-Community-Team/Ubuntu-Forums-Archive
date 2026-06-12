---
title: "[SOLVED] Need to set up a dualHD/dualboot"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by dfinitlydisturbd on 2008-09-21
Just reinstalled Ubu.8 after a major crash.
I have a Win.XP hard drive and a Ubu hard drive.
I can unplug the Ubu. drive and boot windows but Grub doesn't give me the option to boot Win. when both drives are connected.
I have mounted the Win drive and can access it's contents.
How do I get Grub to offer WinXP as a boot option?

---

### Post by 73ckn797 on 2008-09-21
Look at this thread: [http://ubuntuforums.org/showthread.php?t=920862&highlight=super+grub](http://ubuntuforums.org/showthread.php?t=920862&highlight=super+grub)

Download Super Grub (you will have to search), burn to disk and boot system via the disk. It can fix things for you. This is a very quick reply so someone else may need to give further details. I have used this utility on many occasions and it will fix things up.

---

### Post by phidia on 2008-09-21
There's a grub howto [here]("https://help.ubuntu.com/community/GrubHowto") from the Ubuntu wiki. You probably just need to reinstall grub to get it to pick up the XP install-there are additional links at the page I linked here.

---

### Post by richg on 2008-09-21
Might be a little late but here is what I did a few years ago to eliminate hard drive issues. I use a hard drive rack. This photo shows the hd partially out with the keys for locking, plus three more hard drives. The cover is off of one rack.
I have two drives with Ubuntu 8.04 on each. The one marked B is in case the one marked A ever fails. My personal files are backed up on a Firewire external hard drive. It would take me a couple minutes to be back online if a hard drive ever fails.
One hd is Linspire 5.1.427. The fourth hd is Ubuntu 8.04.1 for trying.
One hd, one OS.
I gave away a 98 hd with a PC to my brother.
I installed the new hard drives without formating or partitioning right out of the box. After nearly five years I have never seen any reason to partition a hard drive.
I want to run applications, mot Operating Systems. I do not mess with the OS.
Your mileage may vary.
[IMG]http://i98.photobucket.com/albums/l267/richg1998/Misc/Harddriverack.jpg[/IMG]

Rich

---

### Post by C.S.Cameron on 2008-09-21
I am booting from usb flash drive and have this at the end of my /boot/grub/menu.lst:
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows 2000 Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

It lets me choose between hard disks at grub.

I think the last entry should do you.

---

### Post by 73ckn797 on 2008-09-21
You are welcome. Hope it fixed you up.

If the issue is solved you will need to mark it as such. Click on Thread Tools at the top of this page, where you can mark it from.

---

