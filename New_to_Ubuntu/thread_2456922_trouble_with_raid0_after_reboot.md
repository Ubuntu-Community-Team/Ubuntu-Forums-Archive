---
title: "trouble with raid0 after reboot"
date: 2021-01-21
forum: New to Ubuntu
---

### Post by dakotahross88 on 2021-01-21
Hey all, i've been googling for a few hours and can't find a solution that seems to work (permanently.)

See my issue.
 ```
dymonik@sserver:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdf[5] sde[4] sdd[3] sdc[2] sdb[1] sda[0]
      46883364864 blocks super 1.2 512k chunks


unused devices: <none>
```

then, i do a quick reboot....

```
dymonik@sserver:~$ sudo reboot
[sudo] password for dymonik:
Connection to XXX.XXX.XXX.XXX closed by remote host.
```

after reboot.....

```
dymonik@sserver:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : inactive sde[4](S)
      7813894488 blocks super 1.2


unused devices: <none>
dymonik@sserver:~$
```

ok... strangely, this time it was renamed as md127... which i've seen multiple people have this issue, and they've resolved it.  but if you notice, only one of the original 6 drives is showing up on the raid array...
So, i'm going to reinstall as follows.

```
dymonik@sserver:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : inactive sde[4](S)
      7813894488 blocks super 1.2


unused devices: <none>


dymonik@sserver:~$ sudo umount /dev/md0
[sudo] password for dymonik:
umount: /dev/md0: no mount point specified.


dymonik@sserver:~$ sudo umount /dev/md127
umount: /dev/md127: not mounted.


dymonik@sserver:~$ sudo mdadm --stop /dev/md127


mdadm: stopped /dev/md127
dymonik@sserver:~$ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME                        SIZE FSTYPE            TYPE MOUNTPOINT
loop0                      55.4M squashfs          loop /snap/core18/1932
loop1                      31.1M squashfs          loop /snap/snapd/10707
loop2                      55.4M squashfs          loop /snap/core18/1944
loop3                      69.8M squashfs          loop /snap/lxd/19032
loop4                      67.8M squashfs          loop /snap/lxd/18150
loop5                        31M squashfs          loop /snap/snapd/9721
sda                         7.3T                   disk
sdb                         7.3T                   disk
sdc                         7.3T                   disk
sdd                         7.3T                   disk
sde                         7.3T linux_raid_member disk
sdf                         7.3T                   disk
nvme0n1                   465.8G                   disk
&#9500;&#9472;nvme0n1p1                   1M                   part
&#9500;&#9472;nvme0n1p2                   1G ext4              part /boot
&#9492;&#9472;nvme0n1p3               464.8G LVM2_member       part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   200G ext4              lvm  /


dymonik@sserver:~$ sudo mdadm --zero-superblock /dev/sde


dymonik@sserver:~$ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT


NAME                        SIZE FSTYPE      TYPE MOUNTPOINT
loop0                      55.4M squashfs    loop /snap/core18/1932
loop1                      31.1M squashfs    loop /snap/snapd/10707
loop2                      55.4M squashfs    loop /snap/core18/1944
loop3                      69.8M squashfs    loop /snap/lxd/19032
loop4                      67.8M squashfs    loop /snap/lxd/18150
loop5                        31M squashfs    loop /snap/snapd/9721
sda                         7.3T             disk
sdb                         7.3T             disk
sdc                         7.3T             disk
sdd                         7.3T             disk
sde                         7.3T             disk
sdf                         7.3T             disk
nvme0n1                   465.8G             disk
&#9500;&#9472;nvme0n1p1                   1M             part
&#9500;&#9472;nvme0n1p2                   1G ext4        part /boot
&#9492;&#9472;nvme0n1p3               464.8G LVM2_member part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   200G ext4        lvm  /
dymonik@sserver:~$ sudo nano /etc/fstab




Use "fg" to return to nano.


[1]+  Stopped                 sudo nano /etc/fstab
dymonik@sserver:~$


Use "fg" to return to nano.


[1]+  Stopped                 sudo nano /etc/fstab
dymonik@sserver:~$
```

In sudo nano /etc/fstab   i commented out everything..... ^^^

```
dymonik@sserver:~$ sudo nano /etc/mdadm/mdadm.conf
```

same here....^^^

```
dymonik@sserver:~$ sudo update-initramfs
 -uupdate-initramfs: Generating /boot/initrd.img-5.4.0-62-generic
W: Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast


dymonik@sserver:~$ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
NAME                        SIZE FSTYPE      TYPE MOUNTPOINT
loop0                      55.4M squashfs    loop /snap/core18/1932
loop1                      31.1M squashfs    loop /snap/snapd/10707
loop2                      55.4M squashfs    loop /snap/core18/1944
loop3                      69.8M squashfs    loop /snap/lxd/19032
loop4                      67.8M squashfs    loop /snap/lxd/18150
loop5                        31M squashfs    loop /snap/snapd/9721
sda                         7.3T             disk
sdb                         7.3T             disk
sdc                         7.3T             disk
sdd                         7.3T             disk
sde                         7.3T             disk
sdf                         7.3T             disk
nvme0n1                   465.8G             disk
&#9500;&#9472;nvme0n1p1                   1M             part
&#9500;&#9472;nvme0n1p2                   1G ext4        part /boot
&#9492;&#9472;nvme0n1p3               464.8G LVM2_member part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv   200G ext4        lvm  /


dymonik@sserver:~$ sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=6 /dev/sd[a-f]
mdadm: chunk size defaults to 512K
mdadm: partition table exists on /dev/sda
mdadm: partition table exists on /dev/sda but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sdb
mdadm: partition table exists on /dev/sdb but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sdc
mdadm: partition table exists on /dev/sdc but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sdd
mdadm: partition table exists on /dev/sdd but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sde
mdadm: partition table exists on /dev/sde but will be lost or
       meaningless after creating array
mdadm: partition table exists on /dev/sdf
mdadm: partition table exists on /dev/sdf but will be lost or
       meaningless after creating array
Continue creating array? Y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.


dymonik@sserver:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdf[5] sde[4] sdd[3] sdc[2] sdb[1] sda[0]
      46883364864 blocks super 1.2 512k chunks


unused devices: <none>
```

```
dymonik@sserver:~$ sudo mkfs.ext4 -F /dev/md0
mke2fs 1.45.5 (07-Jan-2020)
/dev/md0 contains a ext4 file system
        last mounted on Thu Jan 21 22:35:56 2021
Creating filesystem with 11720841216 4k blocks and 732553216 inodes
Filesystem UUID: 906e16f3-7e64-46aa-b637-185d6dbdea7e
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544, 1934917632,
        2560000000, 3855122432, 5804752896


Allocating group tables: done
Writing inode tables: done
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done


dymonik@sserver:~$ sudo mkdir -p /mnt/md0


dymonik@sserver:~$ sudo mount /dev/md0 /mnt/md0


dymonik@sserver:~$ df -h -x devtmpfs -x tmpfs


Filesystem                         Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv  196G   16G  171G   9% /
/dev/nvme0n1p2                     976M  198M  712M  22% /boot
/dev/loop0                          56M   56M     0 100% /snap/core18/1932
/dev/loop1                          32M   32M     0 100% /snap/snapd/10707
/dev/loop2                          56M   56M     0 100% /snap/core18/1944
/dev/loop3                          70M   70M     0 100% /snap/lxd/19032
/dev/loop4                          68M   68M     0 100% /snap/lxd/18150
/dev/loop5                          31M   31M     0 100% /snap/snapd/9721
/dev/md0                            44T   24K   42T   1% /mnt/md0


dymonik@sserver:~$ sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
ARRAY /dev/md0 metadata=1.2 name=m5farmsserver:0 UUID=79b042cc:b6595ef4:21e2d64d:340f000e


dymonik@sserver:~$ sudo update-initramfs -u


update-initramfs: Generating /boot/initrd.img-5.4.0-62-generic
W: Possible missing firmware /lib/firmware/ast_dp501_fw.bin for module ast


dymonik@sserver:~$ echo '/dev/md0 /mnt/md0 ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab
/dev/md0 /mnt/md0 ext4 defaults,nofail,discard 0 0
```

```
dymonik@sserver:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdf[5] sde[4] sdd[3] sdc[2] sdb[1] sda[0]
      46883364864 blocks super 1.2 512k chunks



```

seems to have worked? lets check....
```
dymonik@sserver:~$ sudo reboot
Connection to xxx.xxx.xxx.xxx closed by remote host.
```

```
Last login: Thu Jan 21 23:05:42 2021 from xxx.xxx.xxx.xxx
dymonik@sserver:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde[4](S)
      7813894488 blocks super 1.2


unused devices: <none>
dymonik@sserver:~$
```

right back where I started.........

any help would be greatly appreciated!

---

### Post by hikariws on 2021-01-21
I had created 2 RAIDs recently. What I had learned is that we need to manually add the RAID settings to /etc/mdadm/mdadm.conf. If we don't, it uses a random number for md and then fails to mount it as fstab is using md0.

Run `sudo mdadm --detail --scan --verbose` and write its output on /etc/mdadm/mdadm.conf. There are some commands on tutorials that appends it directly, but it fails when ran under sudo instead of real root. Just copy the output and past it.

Use `cat /proc/mdstat` and `sudo mdadm --detail /dev/md0` to see if the RAID is healthy. If it was created properly, no need to recreate it. It's just failing to mount, but it's OK.

---

### Post by TheFu on 2021-01-21
Understand that when just 1 of those 7.3t disks fails, all data on all of them will be gone, right?
Hope you have excellent backups.
The best practice for RAID storage is to create a partition of an exact size always, never use the entire HDD. This way, when a drive fails and a different module with a slightly different size must be used, you aren't screwed. 

Try using **shutdown -r now**.

My mdadm.conf has this line too:
```
CREATE owner=root group=disk mode=0660 auto=yes
```
in addition to the ARRAY lines.

If you just want to mount the array, update the fstab. with a line to do the mount needed. Mounting is never automatic. A correct line in the fstab is mandatory.

---

### Post by dakotahross88 on 2021-01-21
I'm using it as a NVR storage, i wanted to do Raid 10, but that left me with like 6 useable GB.
anyways, now i'm having other issues, as i was posting this thread ^^ rebooting multiple times has caused my server to reboot in Read-Only mode and i cannot do anything. :mad:

---

### Post by hikariws on 2021-01-21
Is ur / mounted on the RAID?

Remember that RAID0 aims to provide better I/O, which any SSD is better. You should write on this RAID0 only temporary files that u have no trouble losing.

---

### Post by dakotahross88 on 2021-01-21
yeah the raid0 is for video storage only. no large issue if i lose it.  I got it out of read only, i commented out one to many things in fstab....  will try the above resolutions now and see if that fixes raid. will update shortly.

---

### Post by dakotahross88 on 2021-01-21
That fixed it, for the most part.... it's booting automatically now, and it's active. But... it repeatedly renames itself as md127

---

