---
title: "disk full? just installed 6hours ago"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by swipisnt on 2013-10-26
hello. ubuntu 12.04 installed 6 hours ago. when i get ubuntu runing i  make update to 12.04.3. now i try to get wot (world of tanks) running, after dowloading all game files and trying to apply and get message - Disk is full. hmh win7 shows i have at least  160gb free space on drive c (ubuntu is on c disk as well) . i read alot of treads about it and i can find solution to my problem coz i m new in this OS.
Pls help me

---

### Post by swipisnt on 2013-10-26
some information
```

swpis@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   16G  1.7G  91% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  984K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  1.1M  3.9G   1% /run/shm
/dev/sda2       294G  128G  166G  44% /host
/dev/sda3       625G   36G  590G   6% /media/Data
swpis@ubuntu:~$ dh -i
The program 'dh' is currently not installed.  You can install it by typing:
sudo apt-get install debhelper

swpis@ubuntu:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/loop0       2271232 221523   2049709   10% /
udev             1017608    570   1017038    1% /dev
tmpfs            1019967    501   1019466    1% /run
none             1019967      3   1019964    1% /run/lock
none             1019967      8   1019959    1% /run/shm
/dev/sda2      174164200 162547 174001653    1% /host
/dev/sda3      618420520  15640 618404880    1% /media/Data

```

---

### Post by ant2 on 2013-10-26
Is this a Wubi install?

---

### Post by oldos2er on 2013-10-26
Is this a Wubi installation? Wubi's limited to 30GB, if I recall correctly.

---

### Post by swipisnt on 2013-10-26
yes it was. was win installer (win7)how can i increase that limit? or wubi is not full installation?

---

### Post by ant2 on 2013-10-26
If you have eaten up 30GB of disk space that quickly maybe you should consider a dedicated partition installation.

---

### Post by swipisnt on 2013-10-26
so what option do i have? uninstal this version and get to full installer?

---

### Post by ant2 on 2013-10-26
> **swipisnt said:**
> so what option do i have? uninstal this version and get to full installer?

It is possible to [increase the size of a Wubi installation]("https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk#Automated_resize"). That runs something along the line of creating a new larger virtual disk and moving the current Wubi installation into it.

A full installation into a dedicated partition is the option** I **would take. However I don't want to lead you into something you don't feel confident with. **Please back up everything and make sure you have Windows recovery disks before you try anything.**

---

### Post by swipisnt on 2013-10-26
yes i try install full version alongside with win7 but i was getting computer restarted and nothing happens, so i though that wubi is the same full installer. ok. thank you very much. going to reinstall full version

---

### Post by ant2 on 2013-10-26
Maybe you should seek some help on here into why your original try at a full installation failed.

---

