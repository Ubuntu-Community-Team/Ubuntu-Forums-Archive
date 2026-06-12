---
title: "Stuck at boot"
date: 2019-07-02
forum: New to Ubuntu
---

### Post by wp.rauchholz on 2019-07-02
Good day community.
I installed Ubuntu (coming from CENTOS) and all went fine.
What happens though from time to time and only in a non-systematic fashion (as I can tell) is that the laptop does not boot, but gets stuck at the LENOVO screen (please see pictures attache).
Switch off and re-booting normally fixes the issue.

Any idea how I can correct this issue?

Thank you very much,


Wolfgang

---

### Post by yancek on 2019-07-02
Did you have CentOS on this computer previously?  Did you repalce it with Ubuntu or is this just a new computer on which you have installed only Ubuntu?  Newer UEFI/GPT?  Have you tried updating the firmware of the system board as it seems to be occurring prior to your getting to Ubuntu?

---

### Post by wp.rauchholz on 2019-07-02
Yes, CENTOS was installed on this laptop also and overwritten by Ubuntu. I had the same issue with CENTOS too.

UEFI/GPT?; I m not sure what you mean by this. 


Yes, firmware is up to date.

The HW is a ThinkPad T470S

Thanks for the help.

Wolfgang

Wolfgang

---

### Post by Andreyshel on 2019-07-02
> [COLOR=#000000]UEFI/GPT?; I m not sure what you mean by this. [/COLOR]

If you are able to boot from livecd., can you show us output of 
```
sudo fdisk -l
```
command?

---

### Post by wp.rauchholz on 2019-07-02
That there is no misunderstanding. Eventually I can boot. When I am stuck, then I switch the laptop off entirely and re-start. Usually it boots normally then.

sudo fdisk -l

Disk /dev/loop10: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 140,7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 88,5 MiB, 92778496 bytes, 181208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 140,7 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 14,8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 8,4 MiB, 8839168 bytes, 17264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 34,6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 byte

---

