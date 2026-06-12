---
title: "HOW TO: Fix Windows MBR , GRUB error with Windows"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by shailendra on 2008-06-08
Hi,

This "HOW TO" will guide you through fixing Windows MBR which has been corrupted by Ubuntu 8.04.

REQUIREMENTS:
1. Ubuntu live CD.
2. Working internet connection.

PROCEDURE:
1. Boot Ubuntu from the live CD.

2. Go to Systems -> Administration -> Software Sources, and enable the "Universe" repositories by selecting the check box.

4. In "Software Sources" add the link of any listed Debian mirrors to download the "ms-sys" package ; such as "mirrors.kernel.org/debian". This package is not included in Ubuntu 8.04 (Hardy Heron), so you need to install it from Debian.

Visit: http://packages.debian.org/etch/i386/ms-sys/download" for list of all mirrors.

3. Go to Application -> Accessories -> Terminal to launch the terminal.

4. Enter the following commands to install "ms-sys" package;  
   sudo apt-get update
   sudo apt-get install ms-sys

5. Type "sudo fdisk -l" to know in which partition Windows in installed. It is mostly the ones with NTFS or FAT32 file system.

6. Now type the following command to fix the MBR; 
   sudo ms-sys -mbr /dev/sdX
   or
   sudo ms-sys -mbr /dev/hdX

   where, sdX and hdX indicate the Windows partition.

   For eg: Windows is on sda1, use sda1 in place of sdX.

7. Reboot your PC.

---

### Post by meierfra. on 2008-06-08
> Windows is on sda1, use sda1 in place of sdX.

No. You need to use "/dev/sda" in this case. Using "/dev/sda1" will overwrite the Windows boot sector, making Windows unbootable.


Also I recommend  not to add  "mirrors.kernel.org/debian" to  "Software Sources". I did that and it gave me problems during the next "update". Just download  the package and intstall it by double clicking.  (or remove "mirrors.kernel.org/debian" from the  "Software Sources" after you installed "ms-sys".

For other ways to fix the MBR click on FixMBR in my signature.

---

### Post by adrian15 on 2008-06-09
> **shailendra said:**
> 
4. In "Software Sources" add the link of any listed Debian mirrors t0 download the "ms-sys" package ; such as "mirrors.kernel.org/debian". This package is not included in Ubuntu 8.04 (Hardy Heron), so you need to install it from Debian.

Visit: http://packages.debian.org/etch/i386/ms-sys/download" for list of all mirrors.


Please remove your howto.

As [I had explained to debian-legal mailing list](http://www.nabble.com/ms-sys-removal-request-td15462196.html#a15462196) ms-sys [contains MBRs which are copyrighted by Microsoft](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=425943#38) and thus it has been [removed from Debian Unstable](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=470678#44).

Soon or later it will be removed from Etch too.

Thank you.

adrian15

---

