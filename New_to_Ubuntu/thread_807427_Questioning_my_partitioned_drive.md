---
title: "Questioning my partitioned drive"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by m_ad on 2008-05-25
I have a laptop running Ubuntu and Ubuntu only, therefore I don't need any extra partitions than what is needed for Ubuntu to run. I just installed it, and am doubting weather or not I partitioned the drive correctly.

A simple question, just needed your guys' expertise :)

```
matt@matt-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

```

---

### Post by ghantoos on 2008-05-25
Can you post the output of ```
df -h
```It's easier do decrypt. : )

Cheers,

---

### Post by m_ad on 2008-05-25
```
matt@matt-laptop:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             107G  2.4G   99G   3% /
varrun               1009M  100K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   52K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
lrm                  1009M   38M  972M   4% /lib/modules/2.6.24-16-generic/volatile

```

---

### Post by ghantoos on 2008-05-25
You just have one big partition that includes your root, home etc.

It's ok. 

What I prefer having, is:
* 1 partition (at least 10G) for the root (/, /usr/, etc.)
* 1 swap (around 2G)
* the rest for /home (useful to share the home folder with multiple distros)
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G  6.2G   13G  33% /
varrun               1014M  148K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  112K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   38M  977M   4% /lib/modules/2.6.24-16-generic/volatile
/dev/sda6             240G  3.2G  224G  1% /home

```Hope this helps,

Cheers,

---

### Post by m_ad on 2008-05-25
I see.. thanks for your help. Appreciate the quick response.

---

