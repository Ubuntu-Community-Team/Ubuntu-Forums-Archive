---
title: "can't resume from suspend (black screen)"
date: 2021-03-18
forum: New to Ubuntu
---

### Post by jack1990 on 2021-03-18
lenovo E540 -- cpu=2.6 Ghz -- ram=12 G -- graphic = nvidia geforce -- hdd=1 T -- ssd = 240 G
os : ubuntu LTS 20.4 and windows 10

my windows 10 and ubuntu 20.04 installed on ssd memory

my root partition is sdb5 and my swap partition is sdb6

when i suspend my laptop When it runs, it will no longer come out from suspension mode!

output of some related commands:

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=772cd8e6-25ea-4b1d-809e-95e96b02dcc9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=8b3d5a6f-9c51-48d7-98a2-a9107f2ff3cc none            swap    sw              0       0
```

```
lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  64,8M  1 loop /snap/gtk-common-themes/1514
loop1    7:1    0  55,5M  1 loop /snap/core18/1988
loop2    7:2    0    51M  1 loop /snap/snap-store/518
loop3    7:3    0  31,1M  1 loop /snap/snapd/11036
loop4    7:4    0   219M  1 loop /snap/gnome-3-34-1804/66
loop5    7:5    0  32,3M  1 loop /snap/snapd/11107
sda      8:0    0 931,5G  0 disk 
&#9500;&#9472;sda1   8:1    0     1G  0 part 
&#9500;&#9472;sda2   8:2    0   100G  0 part 
&#9500;&#9472;sda3   8:3    0   300G  0 part 
&#9500;&#9472;sda4   8:4    0 329,9G  0 part 
&#9500;&#9472;sda5   8:5    0 100,6G  0 part 
&#9492;&#9472;sda6   8:6    0   100G  0 part 
sdb      8:16   0 223,6G  0 disk 
&#9500;&#9472;sdb1   8:17   0   579M  0 part 
&#9500;&#9472;sdb2   8:18   0  99,4G  0 part 
&#9500;&#9472;sdb3   8:19   0     1K  0 part 
&#9500;&#9472;sdb5   8:21   0   116G  0 part /
&#9492;&#9472;sdb6   8:22   0   7,6G  0 part [SWAP]

```

```
sudo swapon /dev/sdb6
swapon: /dev/sdb6: swapon failed: Device or resource busy
```

---

