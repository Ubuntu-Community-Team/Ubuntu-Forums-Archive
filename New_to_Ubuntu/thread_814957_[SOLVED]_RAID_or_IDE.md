---
title: "[SOLVED] RAID or IDE?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by sayakb on 2008-06-01
Is there any way to check whether I'm using the HDD in IDE or RAID mode? My BIOS reflects nothing..
Thanks in advance.

---

### Post by shifty_powers on 2008-06-01
you would have had to specifically set up the computer in raid mode.

what hard disks do you hvae?  raid requires at least two disks of identical sizes..

---

### Post by sayakb on 2008-06-01
This is on a 160GB desktop HDD:
```

glade@Mean-Machine:~$ sudo fdisk -l
[sudo] password for glade: 

Disk /dev/sda: 160.0 GB, 16092480896 bytes
255 heads, 63 sectors/track, 19459 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246        1369      996030   82  Linux swap / Solaris
/dev/sda3            1370        7297   147616660   83  Linux
glade@Mean-Machine:~$ 

```

---

### Post by sayakb on 2008-06-01
Sorry.. Invalid question I guess.. I forgot that I had only 1 HDD on my personal desktop :(

---

### Post by OldTimeTech on 2008-06-01
Just wishing for more, huh???  LOL!!!

---

### Post by sayakb on 2008-06-01
> **OldTimeTech said:**
> Just wishing for more, huh???  LOL!!!

I guess I'm getting used to my college sponsored desktops ..  ;)

---

### Post by OldTimeTech on 2008-06-01
Totally understand....would like to have a raid myself, never have to lose anything....yahoooo!!!  LOL!!

---

### Post by shifty_powers on 2008-06-01
heh happy to help ;)

---

