---
title: "FreeNAS to Ubuntu migration with ZFS"
date: 2021-02-11
forum: New to Ubuntu
---

### Post by laspo on 2021-02-11
Hi all,

My previous setup was FreeNAS OS on USB-stick with three 4TB disks in ZFS (RAIDZ). I'm now migrating to Ubuntu but I'm having difficulty to connect to my disks and retrieve the data.
I've installed Ubuntu Server 20.04.2 LTS and ZFS utility on USB-stick but when I use the commands below, I'm getting stuck. 

zpool list --> [I]no pools available
[/I]
zpool status --> *no pools available*

zpool import --> *cannot discover pools: permission denied*

But when I check my disks with sudo fdisk -l, I can definitely see each disk. For example for the first one (others are identical with sdb and sdc):

[I]Disk /dev/sda: 3.65 TiB etc.
...
Disklabel type: gpt
...
Device        ...   Size   Type   
/dev/sda1   ...   2G     FreeBSD swap
/dev/sda2   ...   3.7T   FreeBSD ZFS[/I]

I've googled for a while now but I can only find that depending on the ZFS versions it might not be possible without wiping all data and recreating the pools. Are there any alternatives?
It seems its more of a permission issue.

Many thanks in advance.

Best regards

---

### Post by laspo on 2021-02-11
Okay, I'm a dumb ass. Need to use sudo ofcourse...

---

