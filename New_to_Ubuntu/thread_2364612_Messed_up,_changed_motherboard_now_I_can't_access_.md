---
title: "Messed up, changed motherboard now I can't access hard drive."
date: 2017-06-25
forum: New to Ubuntu
---

### Post by skrach33 on 2017-06-25
Hi, I'm a bit new with ubuntu (Lubuntu), wanted to change the motherboard so I did. So now it doesn't run (messed up :(), because /home is in a hard drive that can't be accessed. It says it hasn't have apparmor installed. Tried to access it with life lifecd but nothing. 

Problem is that I have information in it and can't get it out. Connected the hard drive to an other pc with lubuntu. Looked in many post and tried many things like running Badblocks, it says there is no problem, then I used testdisk, could get some files out but it copies everything so de hard drive where I copy to gets filled, then I try to eliminate some files to make some space and I don't have permission so I tried with nautilus, I get to eliminate but it ends up in the trash, but I can't empty it even with nautilus, I don't know why. Then I empty it with a command in the terminal, but I tried it another time and the files disappear but the disk is still full. So now I can't access the hard drive and the other one is full. With testdisk I can't make it copy to an external hard drive. 

Is there some one that can help me? I keep trying things and get nowhere.

---

### Post by cariboo on 2017-06-25
Does:

```
sudo fdisk -l
```

list the disk? The output should look similar to this:

```
sudo fdisk -l
[sudo] password for cariboo: 
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6561E15D-8645-4946-991C-E523C5302B0B

Device         Start       End   Sectors   Size Type
/dev/sda1       2048 204802047 204800000  97.7G Linux filesystem
/dev/sda2  204802048 205006847    204800   100M EFI System
/dev/sda3  205006848 468860363 263853516 125.8G Linux filesystem


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 3EF5D577-6C99-4443-A0A2-2444C42BB309

Device         Start        End    Sectors   Size Type
/dev/sdb1       2048  466943999  466941952 222.7G Linux filesystem
/dev/sdb2  512000000  516095999    4096000     2G Linux swap
/dev/sdb3  516096000 1953523711 1437427712 685.4G Linux filesystem
/dev/sdb4  466944000  511999999   45056000  21.5G Linux filesystem

Partition table entries are not in disk order.




Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 2C51CF49-75CD-420D-8BD3-7E1882D7688A

Device     Start        End    Sectors   Size Type
/dev/sdc1   2048 1953525134 1953523087 931.5G Linux filesystem
```

---

### Post by skrach33 on 2017-06-25
This is the result:

```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes








Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe78be78b


Disposit.  Inicio     Start     Final  Sectores   Size Id Tipo
/dev/sda1              2048   7811071   7809024   3,7G 82 Linux swap / Solaris
/dev/sda2  *        7811072 124997631 117186560  55,9G 83 Linux
/dev/sda3         124999678 976771071 851771394 406,2G  5 Extendida
/dev/sda5         124999680 976771071 851771392 406,2G 83 Linux




Disk /dev/sdb: 223,6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xf6c631bf


Disposit.  Inicio     Start     Final  Sectores   Size Id Tipo
/dev/sdb1  *           2048   2000895   1998848   976M 83 Linux
/dev/sdb2           2002942 468860927 466857986 222,6G  5 Extendida
/dev/sdb5           2002944  34000895  31997952  15,3G 82 Linux swap / Solaris
/dev/sdb6          34002944 234000383 199997440  95,4G 83 Linux
/dev/sdb7         234002432 468860927 234858496   112G 83 Linux


Partition 2 does not start on physical sector boundary.




Disk /dev/sdc: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9617deff


Disposit.  Inicio Start      Final   Sectores   Size Id Tipo
/dev/sdc1  *       2048 1953523711 1953521664 931,5G 83 Linux




Disk /dev/sdd: 7,3 GiB, 7807696896 bytes, 15249408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Disposit.  Inicio Start    Final Sectores  Size Id Tipo
/dev/sdd1          8064 15249407 15241344  7,3G  c W95 FAT32 (LBA)
drone@drone-desktop:~$ 
```


I see it says "Partition 2 does not start on physical sector boundary."

What do I do next 8-[

Thanks for answering

---

### Post by skrach33 on 2017-06-29
Cariboo, should I do something, is there more information I should give?

Really don't know what steps I should take.

---

### Post by oldfred on 2017-06-30
Ignore error on start of extended partition as you do not directly write into. It would be important if a primary or logical partition.

You should have a backup drive large enough for all your data that you want to keep.

If Linux formatted you need to know & understand ownership & permissions. 
I use same user fred on all my installs and first user is 1000 internally. And then I set permissions similar to /home for all data partitions so user 1000 has access.

Best just to have a larger drive/partition to copy data into.
Is issue just mounting or is partition corrupted and needs fsck?
Be sure to change example from sdb1 to each of your ext4 partitions.

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Years ago I changed motherboard & system just worked. But similar but newer Intel board & similar but newer nVidia card that used same version of nVidia driver.

Live installer may be a better option as it often lets you see other partitions. Default mount is a bit more permissive.

---

### Post by skrach33 on 2017-06-30
Ok, thanks oldfred, will try my best, I'll tell what happened.

---

### Post by skrach33 on 2017-07-13
Tried to do something's that was mentioned but it wasn't successful or maybe I didn't didn't do it right. Is there a way that I could do step by step?
I have no idea how to solve this.
In advance thanks.

---

### Post by oldfred on 2017-07-13
Have you done backups?

You have 4 Linux partitions per your partition list. sda2, sda5, sdb1 & sdb6.
Did you run the e2fsck as posted but using each of your Linux partitions in place of the sdb1 in example?

---

### Post by skrach33 on 2017-07-25
No I didn't backup, and I think I tried e2fsck, I will try again. Got access with a recovery tool like testdisc, I will search it and post it.

---

