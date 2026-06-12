---
title: "Can't mount partition, get &quot;&lt;partition&gt; device already mounted or &lt;folder&gt; busy&quot;"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by dvks on 2013-04-03
I searched and tried any idea I could find on forums but nothing help
I have Ubuntu 12.10 installed on internal drive partition /dev/sda1 (100GB), have another partition /dev/sda2 (100GB) that to my best knowledge is not being used, have 3rd partition /dev/sda3 (794GB) mounted over /users and additional swap partition /dev/sd4 ( 6GB).
When I try to mount /dev/sda2 on a folder /sysbackup I get error: "mount: /dev/sda2 already mounted or /sysbackup busy"

1. Ran udisks --dump , it show the partitions sda1, sda2 sda3 sda4 as expected and indicate that /dev/sda2 is not mounted and has no mount path and file-system type is ext4
1. Checked /etc/fstab there is nothing with /dev/sda2 or its UUID or /sysbackup, all the other 3 partitions are ok
2. Checked /etc/mtab , same as above
3. Checked /proc/mounts, same as above
4. When I activate nautilus it show the partition under "Devices" on the left bar but when I click on it I get the error:

Unable to mount 100 GB Volume

Error mounting /dev/sda2 at /media/root/cb013233-b1c5-4a17-9e58-69d7389cd961: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda2" "/media/root/cb013233-b1c5-4a17-9e58-69d7389cd961"' exited with non-zero exit status 32: mount: /dev/sda2 already mounted or /media/root/cb013233-b1c5-4a17-9e58-69d7389cd961 busy

I appreciate help since it is beyond my knowledge of Ubuntu
Thanks

---

### Post by dabl on 2013-04-03
It would appear that it is attempting to be mounted at /media/root.  Is there such a mount point?  Is there a line in /etc/fstab that would reflect such a mount point?

In a terminal, issue 

```
sudo mount | grep sda2
``` and post the output here, if there is any (there may be none).

I would also like to see this output:

```
sudo blkid -c /dev/null -o list
```

---

### Post by dvks on 2013-04-03
> **dabl said:**
> It would appear that it is attempting to be mounted at /media/root.  Is there such a mount point?  Is there a line in /etc/fstab that would reflect such a mount point?

In a terminal, issue 

```
sudo mount | grep sda2
``` and post the output here, if there is any (there may be none).

I would also like to see this output:

```
sudo blkid -c /dev/null -o list
```


Thanks for your feedback, 

There is nothing in the feedback from sudo mount that relates either to  sda2 
there is nothing under /media or /media/root 


The output of sudo mount ==> I have the sda1 (UBUNTU partition) and sda3 (mounted on /users) but nothing for sda2.
```

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
cgroup on /sys/fs/cgroup type tmpfs (rw,relatime,mode=755)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu)
cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
/ksnas_users/dov/Documents on /var/www/owncloud/data/dov/files/Documents type none (rw,bind)
/ksnas_users/dov/Downloads on /var/www/owncloud/data/dov/files/Downloads type none (rw,bind)
/ksnas_users/dov/Music on /var/www/owncloud/data/dov/files/Music type none (rw,bind)
/ksnas_users/dov/Pictures on /var/www/owncloud/data/dov/files/Pictures type none (rw,bind)
/ksnas_users/dov/Public on /var/www/owncloud/data/dov/files/Public type none (rw,bind)
/ksnas_users/dov/Videos on /var/www/owncloud/data/dov/files/Videos type none (rw,bind)
/ksnas_users/dov/files_versions on /var/www/owncloud/data/dov/files_versions type none (rw,bind)
/dev/sda3 on /home type ext4 (rw)
/ksnas_users/dov/Documents on /home/dov/Documents type none (rw,bind)
/ksnas_users/dov/Downloads on /home/dov/Downloads type none (rw,bind)
/ksnas_users/dov/Music on /home/dov/Music type none (rw,bind)
/ksnas_users/dov/Pictures on /home/dov/Pictures type none (rw,bind)
/ksnas_users/dov/Public on /home/dov/Public type none (rw,bind)
/ksnas_users/dov/Videos on /home/dov/Videos type none (rw,bind)
/ksnas_users/dov/files_versions on /home/dov/files_versions type none (rw,bind)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
gvfsd-fuse on /run/user/root/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)


```



The output of the blkid ==>

```

device                         fs_type      label         mount point                        UUID
---------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                      ext4                       /                                  c9f5b129-9d95-4683-9487-ef686578fb73
/dev/sda2                      ext4                       (in use)                           cb013233-b1c5-4a17-9e58-69d7389cd961
/dev/sda3                      ext4                       /home                              64ef32ae-1982-4fb3-aa2a-2a3a9f706a79
/dev/sda4                      swap                       <swap>                             e874ca13-6f5e-40be-98ac-ca6783ad2b52

```

Thanks for you help

---

### Post by AlecJ on 2013-04-03
use Gparted to inspect the drive, should give you the information you need

Gparted should be installed, if not

sudo apt-get install gparted

---

### Post by dvks on 2013-04-03
Using gparted doesn't help too much, it actually says that the partition is not mounted.

As I mentioned at the beginning  I used "udisks --dump", following is the part that relates to  "/dev/sda2"
```

Showing information for /org/freedesktop/UDisks/devices/sda2
  native-path:                 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/ata7/host6/target6:0:0/6:0:0:0/block/sda/sda2
  device:                      8:2
  device-file:                 /dev/sda2
    presentation:              /dev/sda2
    by-id:                     /dev/disk/by-id/ata-ST1000LM024_HN-M101MBB_S2R8J9AC903166-part2
    by-id:                     /dev/disk/by-id/scsi-SATA_ST1000LM024_HN-S2R8J9AC903166-part2
    by-id:                     /dev/disk/by-id/wwn-0x50004cf208794f45-part2
    by-id:                     /dev/disk/by-uuid/cb013233-b1c5-4a17-9e58-69d7389cd961
    by-path:                   /dev/disk/by-path/pci-0000:01:00.0-scsi-0:0:0:0-part2
  detected at:                 Wed 03 Apr 2013 02:08:46 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Wed 03 Apr 2013 02:08:46 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        99999547392
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ext4
  version:                     1.0
  uuid:                        cb013233-b1c5-4a17-9e58-69d7389cd961
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    2
    type:                      0x83
    flags:                    
    offset:                    100205068288
    alignment offset:          0
    size:                      99999547392
    label:                     
    uuid:
```

---

### Post by dvks on 2013-04-03
gparted didn't give significant information, but when I tried to use gparted to simply delete the partition, while other tools claimed the partition is mounted gparted didn't complain.
When applied the operation it caused gparted to hang-up.
I did a system restart and it turned out that the partition has been deleted.
Now I recreated it manually and have no problem mounting or un-mounting it so the problem is resolved.

---

### Post by dvks on 2013-04-03
And now I managed replicate the problem, any one has explanation:
I have one drive: /dev/sda
the /dev/sda has 4 primary partitions- /dev/sda1= Ubuntu system, /dev/sda2 = a backup space, /dev/sda3 = user folder, mounted over /users, /dev/sda4 = swap

The strange behavior start if I unmount the /dev/sda2 and shutdown the system when /dev/sda2 in not mounted.
Next time I boot the system the /dev/sda2 becomes trapped as mounted  somewhere on /media/root while in fact it is not mounted anywhere but it is locked and the only way out is to delete it

Any explanation why it happens?
Let me explain the general idea of what I am trying to do, I wish to use /dev/sda2 as a backup space and in order to protect its content I would like to mount it only when a dedicated proprietary backup software need to access the backup content and then unmounts it again, so when the system boot this partition should not be mounted. But as I discovered there is something that tries to mount it over media/root , fail and lock it.

---

### Post by oldfred on 2013-04-04
What software are you using to mount it and unmount it as that sounds like it is the issue. And where are you mounting it.

I use rsync and just check to see if my backup partition exists and mount it, it just gives an error if already mounted, but works. (I should also check if mounted I suppose.)

# ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi
 
mount -t ext3 /dev/sda2 /mnt/backup

---

### Post by dvks on 2013-04-04
oldfred
Thanks for the feedback.
At this point I believe that I know what cause the problem, the question is if I am doing something wrong or it is a bug, here are the details:
1. When I create a new system from a distri USB stick and set the partitions structure manually ( /dev/sda1 mounted on "/", /dev/sda2 not formatted or mounted just a "place holder", /dev/sda3 mounted on /home and /dev/sda4 as swap), or if logout and reboot an existing installation, if I have on the system drive /dev/sda a partition that doesn't have a reference mounting line on /etc/fstab, Fore some reason Ubuntu tries to auto mount such partition on /media/root/<partition UUID> , it fails to do it but the partition remains in a busy state so I can't mount it anywhere else or do anything with it.
The only solution I managed to find is to delete it with gparted, since it is busy I think that the actual delete is done on the next boot so I now boot without the partition, this allow me to create a new one after boot and mount it and add it to /etc/fstab with "noauto" , when done this way it works ok.  
2. The whole story started because I wanted to prepare my system drive /dev/sda manually during the installation with the following partitions- 
       /dev/sda1 = system partition mounted on "/"
       /dev/sda2 = a "place holder" partition to be used later by my backup software that will create the file system and mount it let's say on "/backup" just when need to access it and than unmounts it.
       /dev/sda3 = users partition mounted on "/home"
       /dev/sda4 = swap
As described before everything works ok excluding the /dev/sda2 that becomes busy etc.
Am I doing something wrong? or it is a bug.
I appreciate your time, thanks for your help

---

### Post by oldfred on 2013-04-04
Did you create the partition, but not format it. Then it would not have an UUID and the mounting then fails as there is no UUID. 
But I am not sure the developers will call it a bug as if you create a partition they may assume you format it? But a bios_grub partition is not formatted and works without issue in gpt partitioned drives.

---

### Post by dvks on 2013-04-04
From my point of view as a user the potential bugs are:
1. When I create a new system from a distri USB and during the installation I am prompted to setup my drive's partitions and I choose to do it manually and set a partition marked as "not-used" as one of the options given to me on the selection of the partition file-system type, why Ubuntu even try to mount it and then when failed why it is trapped as busy?
2. When I unmount a partition on my system drive (no LVM or RAID) and do not have it referenced on /etc/mtab why on the next boot Ubuntu tries to mount it on /media/root/UUID, and fail and keep it busy so when the system is up and when needed I try to mount it I can't do it, moreover, from this point the only solution I found was actually to delete it loosing any data I had.

Again, I am not sure if I am doing something wrong or there is a solution to these process.
The solution I am trying now is to leave empty space and create the partition after the system is up and have it marked as "noauto" on the /etc/mtab.
Anyway thanks for your time and your help.

---

### Post by dabl on 2013-04-05
If you want /dev/sda2 mounted, then it needs a filesystem, a mount point, and a mount line in /etc/fstab.  From the posts above, I see no indication that any of these exist.

```
sudo mke2fs -t ext4 /dev/sda2
```

```
sudo mkdir -p /mnt/backup
```

```
sudo mount -t ext4 /dev/sda2 /mnt/backup
```

then issue the first two commands I posted above, to verify that the filesystem is mounted as intended.

---

### Post by dvks on 2013-04-05
During the installation I just wanted to create the partition without file system and without mounting it, the installation offers selection of "not-used" for the file system type but this doesn't work since when you select this option the new partition becomes busy after boot and it is not possible to create a file system and mount it.
The solution is during installation to create all other partitions and leave unallocated space for this additional partition without creating actual partition.
Then after installation is done I use parted command to create the additional partition over the free drive space, create a file system and add a proper line to /etc/fstab with "noauto" option so it is not mounted automatically and I mount it manually when needed.
My conclusion is that there is a bug or at least confusing option on the installation "do something else" for the drive partitioning option, the "not used" option suggest that you can create a partition but set it up later, yet this is impossible since the partition get trapped as busy although it doesn't have any file system and it is  not mounted.

Anyway I would like to thank you for your help and time and I consider this case as resolved

---

### Post by dabl on 2013-04-06
> **dvks said:**
> 
My conclusion is that there is a bug or at least confusing option on the installation "do something else" for the drive partitioning option, the "not used" option suggest that you can create a partition but set it up later, yet this is impossible since the partition get trapped as busy although it doesn't have any file system and it is  not mounted.


I understand, although I don't fully agree.  Ubuntu has done a lot of work to try to make the installation process for the typical use cases easy.  But my view is that inserting so many partitioning options into the Live CD has made installation unnecessarily complicated.  It has always been better, IMHO, to take a Parted Magic, or GParted Live CD, FIRST, and make the needed partitions and filesystems.  Then you can boot the *buntu Live CD or (in former times) Alternate Install CD, and focus strictly on installing the OS, since the partitions already exist as needed.  That is the simpler, and hence better approach, in my opinion.

---

