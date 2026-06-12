---
title: "new kernel will not download correctly"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by KMHartman on 2012-09-25
Hello,
 
For the last several days, I have been updating my system using apt-get, and have been getting an error that the latest kernel update will not download properly. I am using Kubuntu 12.04, KDE 4.9.1. The terminal output is below, from the point the kernel has been downloaded.  Any suggestions greatly appreciated.  FYI, I am not afraid to go digging around in my system, but please be as specific as possible if offering any suggestions.

                   Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.2.0-31-generic-pae i386 3.2.0-31.50 [38.2 MB]
  Fetched 38.2 MB in 10min 42s (59.5 kB/s)                                       
  (Reading database ... 239659 files and directories currently installed.)
  Unpacking linux-image-3.2.0-31-generic-pae (from .../linux-image-3.2.0-31-generic-pae_3.2.0-31.50_i386.deb) ...
  Done.
  dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-31-generic-pae_3.2.0-31.50_i386.deb (--unpack):
   failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-31-generic-pae': No space left on device
  No apport report written because MaxReports is reached already
                                                                dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
  Examining /etc/kernel/postrm.d .
  run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae
  run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae
  Errors were encountered while processing:
   /var/cache/apt/archives/linux-image-3.2.0-31-generic-pae_3.2.0-31.50_i386.deb
  E: Sub-process /usr/bin/dpkg returned an error code (1)
      
Thanks,

K

---

### Post by Bashing-om on 2012-09-25
k, Hi ! Welcome to the forum.

This is indicative of the problem "./boot/vmlinuz-3.2.0-31-generic-pae': No space left on device No apport report written because MaxReports is reached already"

use this command in terminal to see what the usage statistics are:
```
df -h
```perhaps we need to free up some operating space.
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by oldos2er on 2012-09-26
See [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by KMHartman on 2012-09-28
Hello, thanks to both of you. After reading your replies, I checked the boot folder and realized it was too small, so I resized it and that solved the issue.

Thanks

---

