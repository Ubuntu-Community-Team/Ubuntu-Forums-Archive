---
title: "Reinstalled u14.04.1; ran ok; installed packages. Did 'suspend' can't boot. Urg"
date: 2014-10-05
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-10-05
Reinstalled u14.04.1 from live dvd, when selecting install alongside xp option installer only allowed 1TB /dev/sdb with widow recovery partition and backup files no windows os. Then did manual selection and designated root and swap files with ext4 filesystems on /dev/sda using space separate from first installation. Installation was successful and I added packages and then selected 'suspend' to avoid 'shutdown'.

i was unable to recover from 'suspend' ;did cold reboot without success; did same in recovery mode no success; ran fsck option got errors and the computer hung. Now running in live mode and cannot directly access my hds. Terminal ubuntu@ubuntu and df and du only check the live cd. How can I access my hds partitions and files? I was able to run gparted and viewed my hds and file systems with no mount points displayed. I'm at a loss .

---

### Post by sandyd on 2014-10-05
Hi, can you post the output of
```

sudo fdisk -l
sudo parted -l
sudo blkid

```

Thanks!

---

### Post by nu2u904 on 2014-10-05
Thank you sandyd. I have done that; now how do i capture the data to put in code form. This data references the 2nd disk on which I just reinstalled a third copy of u14.04 which I'm now using. How do I access similar data on disk 1 for the two linux systems that are still unbootable?

---

### Post by Vladlenin5000 on 2014-10-06
The commands given should output the results for all drives. You can click'n'hold to select the part of the terminal you want then either right-click and copy or CTRL+SHIFT+C (note the difference).
Then, here, "Go Advanced", press "#" and paste inside it.

---

### Post by nu2u904 on 2014-10-06
Thank you sandyd and nacao.

[CODE     donald@donald-HP-Z400-Workstation:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb5       577G  4.0G  543G   1% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           403M  1.4M  401M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  616K  2.0G   1% /run/shm
none            100M   44K  100M   1% /run/user
donald@donald-HP-Z400-Workstation:~$ sudo fdisk -l
[sudo] password for donald: 
Sorry, try again.
[sudo] password for donald: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b2b3b2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   653709311   326853632    7  HPFS/NTFS/exFAT
/dev/sda2       947404800   976766975    14681088    7  HPFS/NTFS/exFAT
/dev/sda3       653709312   694239231    20264960   83  Linux
/dev/sda4       694241278   947404799   126581761    5  Extended
/dev/sda5       694241280   746393599    26076160   83  Linux
/dev/sda6       746395648   788609023    21106688   83  Linux
/dev/sda7       788611072   800997375     6193152   82  Linux swap / Solaris
/dev/sda8       800999424   803106815     1053696   83  Linux
/dev/sda9       803108864   805292031     1091584   83  Linux
/dev/sda10      805294080   939048959    66877440   83  Linux
/dev/sda11      939051008   947404799     4176896   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x84d31f6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   410243071   205121504+   7  HPFS/NTFS/exFAT
/dev/sdb2       410243072   615043071   102400000   83  Linux
/dev/sdb3       615043072   717443071    51200000   83  Linux
/dev/sdb4       717445118  1953523711   618039297    5  Extended
/dev/sdb5       717445120  1945171967   613863424   83  Linux
/dev/sdb6      1945174016  1953523711     4174848   82  Linux swap / Solaris
donald@donald-HP-Z400-Workstation:~$ sudo parted -l
Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  335GB  335GB   primary   ntfs            boot
 3      335GB   355GB  20.8GB  primary   ext4
 4      355GB   485GB  130GB   extended
 5      355GB   382GB  26.7GB  logical   ext4
 6      382GB   404GB  21.6GB  logical   ext4
 7      404GB   410GB  6342MB  logical
 8      410GB   411GB  1079MB  logical   ext4
 9      411GB   412GB  1118MB  logical   ext4
10      412GB   481GB  68.5GB  logical   ext4
11      481GB   485GB  4277MB  logical   linux-swap(v1)
 2      485GB   500GB  15.0GB  primary   ntfs


Model: ATA WDC WD10EADS-00M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  210GB   210GB   primary   ntfs
 2      210GB   315GB   105GB   primary   ext4
 3      315GB   367GB   52.4GB  primary   ext4
 4      367GB   1000GB  633GB   extended
 5      367GB   996GB   629GB   logical   ext4
 6      996GB   1000GB  4275MB  logical   linux-swap(v1)


donald@donald-HP-Z400-Workstation:~$ sudo blkid
/dev/sda1: UUID="D45ED4995ED475A8" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="0626D61526D60599" TYPE="ntfs" 
/dev/sda3: UUID="43a30144-1875-41e0-9a14-47ecb26b9e8a" TYPE="ext4" 
/dev/sda5: LABEL="/home" UUID="2e57eea9-367e-489f-8e57-1e2396234f34" TYPE="ext4" 
/dev/sda6: UUID="ccffc2a4-30fc-4053-9bf1-9071dbe1f57c" TYPE="ext4" 
/dev/sda8: UUID="8f268b1b-4017-4c3a-ba11-24c7581947f5" TYPE="ext4" 
/dev/sda9: UUID="b8fcc963-4de1-4717-8b00-fb566bcbb5d1" TYPE="ext4" 
/dev/sda10: UUID="d51576f7-1fac-4a5c-8fd5-393ec1f314d2" TYPE="ext4" 
/dev/sda11: UUID="41f7c7a4-08ec-4097-ba94-cb24f9cb64c4" TYPE="swap" 
/dev/sdb1: LABEL="Second Hard Disk" UUID="72BCCDD3BCCD9251" TYPE="ntfs" 
/dev/sdb2: UUID="e72298a5-588a-4a90-93dc-dae7bc56dc20" TYPE="ext4" 
/dev/sdb3: UUID="7b5adcdc-2b06-40b5-b82e-e6bdb8c3e5dd" TYPE="ext4" 
/dev/sdb5: UUID="862bbd8d-b54b-477b-b9b2-542d7df9d995" TYPE="ext4" 
/dev/sdb6: UUID="40617978-ac5b-4907-93ab-57954b280d57" TYPE="swap" 
donald@donald-HP-Z400-Workstation:~$ 
]   [/CODE]

How can I access disk /sda on which is xp and two copies of u14.04 neither of which is butable? Same question when running live dvd ,

---

