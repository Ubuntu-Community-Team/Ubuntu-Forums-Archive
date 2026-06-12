---
title: "lvextend &quot;write error failed: No space left on device&quot;"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by davet13 on 2019-01-28
[FONT=courier new]My root directory has run out of space. I have been trying to extend the space available to my root volume.

lvdisplay output:
[/FONT]```
[FONT=courier new]pciadmin@phabricator2:~$ sudo lvdisplay[/FONT]
[FONT=courier new]  --- Logical volume ---[/FONT]
[FONT=courier new]  LV Path                /dev/phabricator2-vg/root[/FONT]
[FONT=courier new]  LV Name                root[/FONT]
[FONT=courier new]  VG Name                phabricator2-vg[/FONT]
[FONT=courier new]  LV UUID                fcl37J-r6yY-qmxP-8Sxa-lOgi-bduJ-vyze44[/FONT]
[FONT=courier new]  LV Write Access        read/write[/FONT]
[FONT=courier new]  LV Creation host, time phabricator2, 2019-01-23 12:59:28 -0700[/FONT]
[FONT=courier new]  LV Status              available[/FONT]
[FONT=courier new]  # open                 1[/FONT]
[FONT=courier new]  LV Size                5.16 GiB[/FONT]
[FONT=courier new]  Current LE             1320[/FONT]
[FONT=courier new]  Segments               2[/FONT]
[FONT=courier new]  Allocation             inherit[/FONT]
[FONT=courier new]  Read ahead sectors     auto[/FONT]
[FONT=courier new]  - currently set to     256[/FONT]
[FONT=courier new]  Block device           252:0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]  --- Logical volume ---[/FONT]
[FONT=courier new]  LV Path                /dev/phabricator2-vg/swap_1[/FONT]
[FONT=courier new]  LV Name                swap_1[/FONT]
[FONT=courier new]  VG Name                phabricator2-vg[/FONT]
[FONT=courier new]  LV UUID                GNK5cA-qbcy-jSr8-vk4t-wVZ7-HPmF-gD9mYG[/FONT]
[FONT=courier new]  LV Write Access        read/write[/FONT]
[FONT=courier new]  LV Creation host, time phabricator2, 2019-01-23 12:59:28 -0700[/FONT]
[FONT=courier new]  LV Status              available[/FONT]
[FONT=courier new]  # open                 2[/FONT]
[FONT=courier new]  LV Size                4.36 GiB[/FONT]
[FONT=courier new]  Current LE             1117[/FONT]
[FONT=courier new]  Segments               1[/FONT]
[FONT=courier new]  Allocation             inherit[/FONT]
[FONT=courier new]  Read ahead sectors     auto[/FONT]
[FONT=courier new]  - currently set to     256[/FONT]
[FONT=courier new]  Block device           252:1[/FONT]

```

df output:[FONT=courier new]
[/FONT]```
[FONT=courier new]pciadmin@phabricator2:~$ sudo df[/FONT]
[FONT=courier new]Filesystem                        1K-blocks    Used Available Use% Mounted on[/FONT]
[FONT=courier new]udev                                2127356       0   2127356   0% /dev[/FONT]
[FONT=courier new]tmpfs                                429480    6108    423372   2% /run[/FONT]
[FONT=courier new]/dev/mapper/phabricator2--vg-root   5166504 5150120         0 100% /[/FONT]
[FONT=courier new]tmpfs                               2147392       0   2147392   0% /dev/shm[/FONT]
[FONT=courier new]tmpfs                                  5120       0      5120   0% /run/lock[/FONT]
[FONT=courier new]tmpfs                               2147392       0   2147392   0% /sys/fs/cgroup[/FONT]
[FONT=courier new]/dev/xvda1                           482922   58225    399763  13% /boot[/FONT]
[FONT=courier new]tmpfs                                429584       0    429584   0% /run/user/1000[/FONT]

```

pvdisplay output:
```
[FONT=courier new]pciadmin@phabricator2:~$ sudo pvdisplay[/FONT]
[FONT=courier new]  --- Physical volume ---[/FONT]
[FONT=courier new]  PV Name               /dev/xvda5[/FONT]
[FONT=courier new]  VG Name               phabricator2-vg[/FONT]
[FONT=courier new]  PV Size               9.52 GiB / not usable 2.00 MiB[/FONT]
[FONT=courier new]  Allocatable           yes (but full)[/FONT]
[FONT=courier new]  PE Size               4.00 MiB[/FONT]
[FONT=courier new]  Total PE              2437[/FONT]
[FONT=courier new]  Free PE               0[/FONT]
[FONT=courier new]  Allocated PE          2437[/FONT]
[FONT=courier new]  PV UUID               zT75Qa-ZU2C-uEes-WhCS-aEe3-joyw-PGKexG[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]  --- Physical volume ---[/FONT]
[FONT=courier new]  PV Name               /dev/xvda3[/FONT]
[FONT=courier new]  VG Name               phabricator2-vg[/FONT]
[FONT=courier new]  PV Size               9.06 GiB / not usable 1.34 MiB[/FONT]
[FONT=courier new]  Allocatable           yes[/FONT]
[FONT=courier new]  PE Size               4.00 MiB[/FONT]
[FONT=courier new]  Total PE              2319[/FONT]
[FONT=courier new]  Free PE               2319[/FONT]
[FONT=courier new]  Allocated PE          0[/FONT]
[FONT=courier new]  PV UUID               dDHJtE-agLF-tcAo-kCrG-07ji-Dl8e-XNMgYd[/FONT]

```

vgdisplay output:
```
[FONT=courier new]pciadmin@phabricator2:~$ sudo vgdisplay[/FONT]
[FONT=courier new]  --- Volume group ---[/FONT]
[FONT=courier new]  VG Name               phabricator2-vg[/FONT]
[FONT=courier new]  System ID[/FONT]
[FONT=courier new]  Format                lvm2[/FONT]
[FONT=courier new]  Metadata Areas        2[/FONT]
[FONT=courier new]  Metadata Sequence No  5[/FONT]
[FONT=courier new]  VG Access             read/write[/FONT]
[FONT=courier new]  VG Status             resizable[/FONT]
[FONT=courier new]  MAX LV                0[/FONT]
[FONT=courier new]  Cur LV                2[/FONT]
[FONT=courier new]  Open LV               2[/FONT]
[FONT=courier new]  Max PV                0[/FONT]
[FONT=courier new]  Cur PV                2[/FONT]
[FONT=courier new]  Act PV                2[/FONT]
[FONT=courier new]  VG Size               18.58 GiB[/FONT]
[FONT=courier new]  PE Size               4.00 MiB[/FONT]
[FONT=courier new]  Total PE              4756[/FONT]
[FONT=courier new]  Alloc PE / Size       2437 / 9.52 GiB[/FONT]
[FONT=courier new]  Free  PE / Size       2319 / 9.06 GiB[/FONT]
[FONT=courier new]  VG UUID               jiyC26-q1Q4-huAX-l7iM-UIEE-3Jcv-E0CiLg[/FONT]

```

When I try to run lvextend on root, I get the following error:
```
[FONT=courier new]pciadmin@phabricator2:~$ sudo lvextend -L+8G /dev/phabricator2-vg/root[/FONT]
[FONT=courier new]  /etc/lvm/archive/.lvm_phabricator2_2193_124559942: write error failed: No spac[/FONT][FONT=&amp]e left on device[/FONT]
[FONT=courier new]  Volume group "phabricator2-vg" metadata archive failed.[/FONT]

```

I'm not sure what I'm missing.

---

### Post by Dennis N on 2019-01-28
Delete or move some files from root to make room to write additions to /etc/lvm/archive 

Then, when extending the lv, you have to resize the filesystem too. Try:
```
 sudo lvextend --resizefs --extents= +2000 /dev/phabricator2-vg/root
```
This adds 2000 of the 2319 free extents, which is about 8 GB, and resizes the file system at the same time.

---

