---
title: "Partitions numbers? ids?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by shadows123 on 2008-07-17
Hey, i needed for my boot.ini ( because of hal.dll problem ) to get the windows partition id.
Here's what fdisk's list gives me.
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2     1505778   102392836    f  W95 Ext'd (LBA)
/dev/sda2   *     1505898     3011780   102400000    7  HPFS/NTFS
/dev/sda3         4165800     4596635    29296848   83  Linux
/dev/sda4         4136388     4165799     2000016   82  Linux swap / Solaris
**/dev/sda5               2     1505778   102392832    7  HPFS/NTFS**

Partition table entries are not in disk order

```
the fat one is my windows, now what's his number? 5 from sda 5 or 7 from id?
What does the thing means ( partition table entries are not in disk order? )
Okay,
thanks a lot :)

---

### Post by shadows123 on 2008-07-17
thought that it would be clearer with a screenshot of gparted ( as i said dev/sda5 is my windows xp. )
Thanks again.

---

### Post by Bachstelze on 2008-07-17
7 identifies the type of the partition. You can find a list of all types [here](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html).

Note that in most cases, this has absolutely **nothing** to do with the **filesystem** that is on the partition (if any).

---

### Post by shadows123 on 2008-07-17
ah ok, so my partition number is five, thanks ^^

---

### Post by coffeecat on 2008-07-17
sda2 would be your Windows C: partition. It has the boot flag set and it is a primary partition. The other NTFS (Windows filesystem) partition is sda5 which is a logical partition held in the 'container' of the extended partition sda1. Windows cannot boot from a logical partition (Linux can, of course :cool:) so the NTFS sda5 partition can only be used for data storage in Windows. It's probably your D:, E:, or F: drive in Windows.

> Partition table entries are not in disk ordermeans exactly that. Look at the numbers from your fdisk output. sda4 occupies earlier sectors that sda3. Also, you've got great empty chunks on the disc.

---

### Post by shadows123 on 2008-07-17
yea "normally" but my pc's kinda messed up you see, as boot it uses the sda 2 like you said, yes, but my windows is installed at sda5 - sda2's boot tells the boot.ini to launch sda5 you see? =)
thanks for the help =)

---

### Post by hyper_ch on 2008-07-17
in the boot ini it should be partition "4". At least grub starts counting with 0 so sda5 would be nr. 4

---

### Post by shadows123 on 2008-07-17
hmm 'sweird but i checked /dev/sda and i found out i'm right, but your explanation does make sense lol :P
i'll try with sda 4 thanks.

---

### Post by shadows123 on 2008-07-18
Thanks a lot, it works now! :D
resolution of problem: edit boot.ini to partition number 4 :).

---

