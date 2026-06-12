---
title: "Ubuntu freeze when idle"
date: 2019-04-21
forum: New to Ubuntu
---

### Post by nmc1998 on 2019-04-21
Recently, my new install Ubuntu 18.04 freeze when the laptop idle, haven't found any solution for this problem with not_AMD chipset laptop, any suggestions for me?
Thank you!
Btw, im using UX430UNR laptop with i5-8250U with Nvidia MX150

---

### Post by dino99 on 2019-04-21
To grab some relative reason(s) about that issue, you can do:

- from the terminal, type: journalctl (for actual session) or journactl -b (for previous one). And search the warning lines (bright white ones) and the error lines (red ones).
- if you still can use the keyboard (when frozen), load 'system-monitor' or htop to see which process to blame.

As you suggest a fresh install (and not a dist-upgrade), tell us how you have made that installation (default proposed choices/manual custom ones ?), and which kind of flavor is it (gnome/kde/...).
Have you set a swap partition ? (deprecated, as now a file swap is used instead).  

Please post the output of: >  sudo fdisk -l

---

### Post by nmc1998 on 2019-04-21
When my laptop frozen, it's completely FROZEN. I cant do anything or use mouse or touchpad, keyboard, .... The only thing i can do is Hard Shutdown by keep pressing the Turnoff button and using Alt+SysRq+REISUB to reboot it
Anyways, here is the out put of 'sudo fidsk -l'
```
Disk /dev/loop0: 34,6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 3,7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 140,7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 14,5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 147,3 MiB, 154406912 bytes, 301576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 2,3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B2B0954B-968C-43BA-A68D-6D9C37526BC1


Device        Start       End   Sectors   Size Type
/dev/sda1      2048   1050623   1048576   512M EFI System
/dev/sda2   1050624  40112127  39061504  18,6G Linux filesystem
/dev/sda3  40112128  63549439  23437312  11,2G Linux swap
/dev/sda4  63549440 500117503 436568064 208,2G Linux filesystem




Disk /dev/loop8: 127 MiB, 133103616 bytes, 259968 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```



Btw, my PC frozen twice while i typing this reply T.T

I realized that when my laptop idle, its going to freeze after about 1-2 minutes

---

