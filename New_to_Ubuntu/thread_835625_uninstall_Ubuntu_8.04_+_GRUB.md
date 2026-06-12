---
title: "uninstall Ubuntu 8.04 + GRUB"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by taffypride on 2008-06-20
Just installed Ubuntu 8.04 onto my second hdd and found some things don't work and I've not been able to find solutions to fix them.

So what I want to do is uninstall Ubuntu and also remove the GRUB bootloader from my system and go back to using XP Home on my primary hdd.

Problem....getting rid of Ubuntu is easy - just zap the hdd in Windows.  Doesn't remove GRUB - keep getting a GRUB Error 17 code come up and won't get any further with bootup.

Problem....no XP Recovery Disc - wasn't supplied with the machine when I bought it second hand and I can't get hold of a copy at the moment.

So just how do I remove the GRUB bootloader from my system?  Google comes up with using the FDISK /mbr command - but there appears to be various results of that - most of which say it doesn't work.

I've even attempted to use System Restore in XP to go back to the last restore point I did thinking that might restore the master boot record - nope.

All I want to do is get rid of all traces of Linux from this machine without trying to reinstall XP.

Please help someone - I'm tearing my hair out here.

Either help with this problem or can someone tell me how I can get my Huawei E169G USB data modem (on the 3 network) configured and working correctly in Ubuntu 8.04 and then point me in the correct direction for Windows application emulation under Linux.

Many thanks - and sorry it's a long post.

---

### Post by bodhi.zazen on 2008-06-20
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

wubi : [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by ruffEdgz on 2008-06-20
Well that sucks that you don't have a CD because that would make life so much better :D

I would check out bootdisk.com to help you get to the DOS part by downloading 'XP Quick Boot Diskette' from the list to the link provided: [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

From there you will have to type in the command:

```
fixmbr 
```
or
```
fdisk /mbr
```

I know there are a mixture of people saying it does or doesn't work but those are the commands that you need to run if you are in DOS mode.

The other option would be to get into your windows partion somehow and edit the boot.ini file:

[http://support.microsoft.com/?kbid=314081](http://support.microsoft.com/?kbid=314081)

Hope that helps!

---

### Post by Duck2006 on 2008-06-20
The mbr can be fixed from the ubuntu live cd if you have already deleted the ubuntu partition and not fixed the mbr.

[http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

---

