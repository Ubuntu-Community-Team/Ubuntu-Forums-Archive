---
title: "A few doubts about partitions and networks"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by jma79 on 2008-10-10
So, after installing and playing around a little bit with xubuntu i found 2 situations that i'm unable to solve.

- Xubuntu only "sees" 1 partition, the one that it occupies. I can't reach the other partitions i have, namely windows.

- I'm unable to create a network with my laptop that runs ubuntu. This is important since i really needed to move files between the two computers.

Thanks in advance

---

### Post by tarps87 on 2008-10-10
Can you post the output off ```
sudo fdisk -l
```(lower case L)
Are you trying to create a wire or wireless network?
For windows shares you will need to use samba```
sudo apt-get install samba
```should install samba, it you have an internet connection.
pyneighborhood will be useful for browsing networks in Xubuntu.
If you can describe where you are having the problems with the network it will be easier to give more precise help

---

### Post by jma79 on 2008-10-10
Here's the result:

Disk /dev/sda: 9115 MB, 9115361280 bytes
255 heads, 63 sectors/track, 1108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04470446

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1107     8891946    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c75247b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4844    38909398+   7  HPFS/NTFS
/dev/sdb2            4889       19457   117025492+   f  W95 Ext'd (LBA)
/dev/sdb3            4845        4888      353430   83  Linux
/dev/sdb5            4889        9713    38756781    7  HPFS/NTFS
/dev/sdb6            9714       14567    38989723+   7  HPFS/NTFS
/dev/sdb7           14568       16709    17205583+   7  HPFS/NTFS
/dev/sdb8           16710       19388    21519036   83  Linux
/dev/sdb9           19389       19457      554211   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1073 MB, 1073742336 bytes
255 heads, 63 sectors/track, 130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d0c0b0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         130     1044193+   b  W95 FAT32

The problem with the wired network is that i can't connect the two computers.
I using ubuntu gutsy in my laptop and xubuntu hardy on the desktop. When I use windows in the desktop all ihave to do is connect and ubuntu recognises the network and shared folders automatically. I even use the internet connection that's configured in windows.
When using xubuntu, i can't detect the other computer, but since i'm a new user of this systems, probably i'm missing something here.

Thx

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

### Post by tarps87 on 2008-10-13
It looks like you have 5 NTFS partition, is this what you expect? They should all be visible in windows. Try ```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1
```
This should mount the first hard drive in /media/sda1, I will only mount it in read mode, ntfs-3g should mount it in read/write mode.
Can you create a share on the Xubuntu machine and see it from the Ubuntu machine, It is possible there is a difference in the samba configurations. A small GUI for configuring samba is call samba and can be found it add programs, the is a more advanced on call gsamba also found in synaptic. There is also this doc on setting up samba, For me using samba between to machines running Ubuntu usaly take a long to find shares than between Ubuntu and Windows.
This should list all samba shares on the network```
smbtree
```

---

