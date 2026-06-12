---
title: "Replace Ubuntu 19.10 with 18.04 - need gcc-mipsel-linux-gnu package"
date: 2020-03-22
forum: New to Ubuntu
---

### Post by w02070104 on 2020-03-22
Good afternoon. I am trying to install the package gcc-mipsel-linux-gnu for ubuntu 19.10, distribution eoan. 
I have already checked the ubuntu packages and unfortunately I can't find anything. 
Can i find another way to have this package? 
I was thinking to remove this ubuntu version and install the 19.04 but I am not confindent in my abilities. 
I need to have that package for a school project. 

Is there something else i can do? 
Thanks for the attention given.

---

### Post by jeremy31 on 2020-03-22
Moved to New to Ubuntu

---

### Post by coffeecat on 2020-03-22
It seems that the package you are looking for is currently only available for 16.04, 18.04 and 19.04.  See: [https://packages.ubuntu.com/search?keywords=gcc-mipsel&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=gcc-mipsel&searchon=names&suite=all&section=all)

> **w02070104 said:**
> I was thinking to remove this ubuntu version and install the 19.04 but I am not confindent in my abilities. 
I need to have that package for a school project.

Don't do that. 19.04 has passed end-of-life and is now unsupported. If the repositories for 19.04 are still open, they will soon close. If you really need to install a release of Ubuntu older than 19.10 in order to be able to get gcc-mipsel-linux-gnu, then the best choice would be 18.04.

A word of explanation. The even numbered releases, released in April, are long-term support (LTS), supported for several years. Currently these are 16.04 and 18.04, and they will be joined by 20.04 when this is released this coming April. 16.04 has only about a year of support left, hence 18.04 would be a better choice. All others, including 19.04 and 19.10, are interim releases supported for only nine months. 19.10 will become end of life in July this year.

If you need help replacing 19.10 with 18.04, post back with some more details of what you are not confident about, and I am sure someone can help you. If this is the path you want to take, I'll change the thread title for you so that you don't have to open another thread.

---

### Post by w02070104 on 2020-03-22
Yes, if someone can help me through this process and install the 18.04 version of ubuntu that would be great. 
Thank you.

So is it possible to replace this ubuntu version with the 18.04, without doing all the process?

---

### Post by ajgreeny on 2020-03-22
let's see more info about your hardware and exactly what is currently installed
The output of command ```
lsb_release -dc && echo "Desktop:	$DESKTOP_SESSION" && uname -mrn
``` will tell us quite a lot about your OS, and output from ```
inxi -Fxz
``` will tell us about your hardware.
Finally output of ```
sudo fdisk -l
``` will give us info about the partitioning on the machine.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when you copy and paste. See my signature below for a **How-to**

---

### Post by w02070104 on 2020-03-22
```
lsb_release -dc && "Desktop: 
> DESKTOP_SESSION" && uname -mrn
Description:	Ubuntu 19.10

Codename:	eoan
Desktop: 
DESKTOP_SESSION: command not found
```

```
sudo fdisk-l
Disk /dev/loop0: 91,38 MiB, 95805440 bytes, 187120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 54,66 MiB, 57294848 bytes, 111904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 54,64 MiB, 57274368 bytes, 111864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop3: 4,2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop4: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop5: 91,32 MiB, 95748096 bytes, 187008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop6: 14,77 MiB, 15466496 bytes, 30208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop7: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 465,78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: WDC WD5000LPCX-6
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6EA390FF-E9AC-4B2F-BCBB-8A4294E5D0BC

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1085439   1083392   529M Windows recovery environment
/dev/sda2    1085440   1290239    204800   100M EFI System
/dev/sda3    1290240   1323007     32768    16M Microsoft reserved
/dev/sda4    1323008 515973119 514650112 245,4G Microsoft basic data
/dev/sda5  515973120 519972863   3999744   1,9G Linux swap
/dev/sda6  519972864 976771071 456798208 217,8G Linux filesystem

Disk /dev/loop8: 156,7 MiB, 164290560 bytes, 320880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop9: 14,76 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop10: 4,26 MiB, 4464640 bytes, 8720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop11: 120,74 MiB, 126582784 bytes, 247232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop12: 152,67 MiB, 160071680 bytes, 312640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop13: 160,16 MiB, 167931904 bytes, 327992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop14: 44,9 MiB, 47063040 bytes, 91920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop15: 55,41 MiB, 58089472 bytes, 113456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop16: 44,18 MiB, 46325760 bytes, 90480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by coffeecat on 2020-03-22
@w02070104, I've edited your thread title to better reflect the help you need now.

Good luck!

---

### Post by him610 on 2020-03-22
First command from Post #5 was....
```

lsb_release -dc && echo "Desktop:$DESKTOP_SESSION" && uname -mrn

```
Try it again.

---

### Post by w02070104 on 2020-03-23
```
Description:	Ubuntu 19.10Codename:	eoan
Desktop:ubuntu
alpaca-machine 5.3.0-42-generic x86_64
```




I was wondering, if it's possible to keep the same grub I have, keep the partition made, delete ubuntu and then replace ubuntu 19.10 with 18.94 on the free partition. Is it doable?

---

