---
title: "Deleted GRUB. Vista will no longer boot"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by AllPowerfulOz on 2008-09-07
Hi guys. I decided to get rid of ubuntu on my dad's laptop (going to be putting it onto my own computer when get it) so I deleted its partitions. Now whenever I try to boot, I get an error message "Grub boot loader failed. Error 22." (Not sure about the exact wording, but that was the error number). Vista recovery disc won't fix it because it says "Boot from HD was successful" or something similar. Does the ubuntu CD have a option to just install the GRUB boot loader? And would that work? Any help would be greatly appreciated. :(

---

### Post by AllPowerfulOz on 2008-09-07
Bumo. Also, the exact message I get when I try to boot is "GRUB Loading stage 1.5.

GRUB loading, please wait...
Error22

---

### Post by lukjad on 2008-09-07
Try this link:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-09-07
If you have the Vista Recovery CD/DVD, which it sounds like you do, boot it up and go into the recovery console/command line and run:
```
bootrec /fixmbr
```
That will reinstall the Vista master boot record (MBR) and overwrite Grub. Let me know how it goes.

---

