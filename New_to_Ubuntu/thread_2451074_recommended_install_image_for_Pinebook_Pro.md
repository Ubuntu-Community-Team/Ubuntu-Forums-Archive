---
title: "recommended install image for Pinebook Pro?"
date: 2020-09-26
forum: New to Ubuntu
---

### Post by applebananacarrot on 2020-09-26
I recently picked up a Pinebook Pro. [https://www.pine64.org/pinebook-pro/](https://www.pine64.org/pinebook-pro/)

The laptop comes with a Manjaro/Arch distro, and I'd prefer to run ubuntu on the system. Wondering if there's a recommended ("official") install image/ISO for lightweight arm systems like this. Also not sure what the install procedure would be for a laptop with USB ports, an SD card slot, and no external drives.  

Relevant hardware specs are: 

>uname -a
Linux WhitePine 5.8.6-1-MANJARO-ARM #1 SMP Thu Sep 3 22:01:08 CEST 2020 aarch64 GNU/Linux

>df -h
Filesystem      Size  Used Avail Use% Mounted on
dev             1.9G     0  1.9G   0% /dev
run             1.9G  1.4M  1.9G   1% /run
/dev/mmcblk2p2   58G  9.0G   46G  17% /
tmpfs           1.9G   36M  1.9G   2% /dev/shm
tmpfs           4.0M     0  4.0M   0% /sys/fs/cgroup
tmpfs           1.9G  8.0M  1.9G   1% /tmp
/dev/mmcblk2p1  214M   70M  144M  33% /boot
tmpfs           380M   64K  380M   1% /run/user/1000

 cat /proc/meminfo 
MemTotal:        3886508 kB
MemFree:         1560316 kB
MemAvailable:    2298672 kB

cat /proc/cpuinfo 
...
processor       : 5
BogoMIPS        : 48.00
Features        : fp asimd evtstrm aes pmull sha1 sha2 crc32 cpuid
CPU implementer : 0x41
CPU architecture: 8
CPU variant     : 0x0
CPU part        : 0xd08
CPU revision    : 2

---

### Post by TheFu on 2020-09-26
That's specialized HW. Best to stick with distros you find on their support website.
Other Pine64 OSes weren't generic either. Only expect distros created for the platform to make use of the hardware.

Of course, if you are a developer, then you could build a custom ARM distro yourself.

Google found this debian distro installer: [https://github.com/daniel-thompson/pinebook-pro-debian-installer](https://github.com/daniel-thompson/pinebook-pro-debian-installer)

---

### Post by mc4man on 2020-09-30
[https://wiki.pine64.org/index.php?title=Pinebook_Pro_Software_Release](https://wiki.pine64.org/index.php?title=Pinebook_Pro_Software_Release)

---

