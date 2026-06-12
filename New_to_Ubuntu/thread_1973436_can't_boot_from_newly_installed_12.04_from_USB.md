---
title: "can't boot from newly installed 12.04 from USB"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by rvanegas1 on 2012-05-04
I have tried to install 12.04 LTS from a USB installer, using specifically the amd64 desktop binary. Installation proceeded well enough as far as the point when the installer requires a restart. But then on reboot, I found myself back in Windows 7. I can still start live Ubuntu from the USB drive, when it is plugged in during reboot, but I cannot start the installed Ubuntu on my hard drive.

I have plenty of experience with the terminal, unix, and even older versions of Linux back more than a decade. But I haven't had to install a Linux distro in years, so I feel like newbie once more. 

This is an HP p2-1013w based on an AMD E-450 APU and 3GB of memory.

Any help appreciated!

---

### Post by 2ta8gdfte on 2012-05-04
Using the usb booted to the ubuntu desktop download this script extract it to your desktop and run this command and pastebin the results text 

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)    

 sudo bash ~/Desktop/bootinfoscript

You may be able to read the script and see you're just missing grub in the mbr. Here is a chroot to load it.

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

---

### Post by rvanegas1 on 2012-05-05
Thank you for the help!  Here's the look of my system according to bootinfoscript.

[http://pastebin.com/XvCATgS7](http://pastebin.com/XvCATgS7)

Sure enough, the MBR is still just Windows, so I tried following the chroot instructions, but I stumbled on step 6. See the second pastebin.

[http://pastebin.com/mAkkqKXM](http://pastebin.com/mAkkqKXM)

---

### Post by rvanegas1 on 2012-05-05
My mistake, I was trying to mount /dev/sda4 instead of /dev/sda5.

I now am able to run "grub-install /dev/sda" and even successfully recheck after that, but bootinfoscript still says that MBR of /dev/sda is Windows.

---

### Post by westie457 on 2012-05-05
Hi another way for you to try, this has worked for me in the past.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

A How-to on purging and reinstalling Grub.

EDIT:

Had a look at the second link posted by '2ta8gdfte' and in there is mentioned 'Boot-repair'. This fixes most boot issues automatically.

---

### Post by rvanegas1 on 2012-05-06
Thank you both. In the end what worked was the "purge & reinstall" method from the community help page for Grub2.

---

