---
title: "No Write Permissions on my File System"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by PaulM1985 on 2008-07-05
Hi

I only installed Ubuntu yesterday and so I am not completely sure how everything works yet.

I first noticed the problem when trying to write to my external hard drive. I managed to mount it ok using the $sudo mount /dev/sdb1 /media/sdb1 command in the Terminal, but I was unable to write to it in the File Browser.  I checked the permissions and it said that only "Owner : root" has Read/Write access.  

I then checked this for my computer's file system and the same permissions applied.

Is there a way that I can change this so that I have read/write access to my file system and external hard drive.

Paul

---

### Post by bumanie on 2008-07-05
What is the drive formatted to? If it's ntfs > sudo apt-get install ntfs-3g then > sudo apt-get install ntfsconfig The go to Applications --> System Tools and click on ntfsconfig and fill in the  box on the window that appears.

---

### Post by drs305 on 2008-07-05
Do you know the type of formatting the disk has (ext3, ntfs, fat32)?

If it is an ntfs-formatted drive, install ntfs-config:
```
sudo aptitude install ntfs-config
```

Then run it via System Tools, NTFS Configuration Tools. It will run a simple program to mount ntfs drives and include an entry in fstab to automount the partition with you as the owner.

If it's ext3, you can add an entry into fstab to do the same thing.

To solve your immediate problem (ownership), you can run this:
```

sudo chown -R yourusername /dev/sdb1

```

For long term solutions, please post:
```
sudo blkid
sudo cat /etc/fstab
sudo fdisk -l  # (small L)
```

---

### Post by PaulM1985 on 2008-07-05
Thanks for the quick response:

paul@paul-desktop:~$ sudo blkid
/dev/sda1: UUID="723862DD38629FB9" TYPE="ntfs" 
/dev/sda5: UUID="26a9e71d-486d-48d4-9d49-3d0ab08dece6" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="72f1dc91-2a75-40a9-ac55-23137138f148" 
/dev/sdb1: LABEL="SEA_DISC" UUID="0000-0E48" TYPE="vfat" 
paul@paul-desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda5
UUID=26a9e71d-486d-48d4-9d49-3d0ab08dece6  /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda6
UUID=72f1dc91-2a75-40a9-ac55-23137138f148  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda5                                  /media/sda5     ext3         defaults                    0  0  
/dev/sda6                                  /media/sda6     swap         defaults                    0  0  
/dev/sda1                                  /media/sda1     ntfs         defaults                    0  0  
/dev/sdb1                                  /media/sdb1     vfat         defaults                    0  0  
paul@paul-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24fb31ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2335    18755856    7  HPFS/NTFS
/dev/sda2            2336        4865    20322225    5  Extended
/dev/sda5            2336        4754    19430586   83  Linux
/dev/sda6            4755        4865      891576   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

Does this help?
Paul

---

### Post by drs305 on 2008-07-05
This should make your drive automount on boot and make you the owner:

Make sure the mountpoint /media/sdb1 exists.

Backup fstab and open for editing:
```

sudo cp /etc/fstab /etc/fstab.backup
sudo gedit /etc/fstab

```

Put a # in front of this line to make it a comment (not read):
```

**#** /dev/sdb1 /media/sdb1 vfat defaults 0 0 

```

Replace with:
```

dev/sdb1 /media/sdb1 vfat utf8,uid=1000,gid=100,umask=027 0 0

```

Now try it:
```
sudo umount /dev/sdb1
sudo mount /dev/sdb1
```

Once you are sure it works, you could replace the device name with the label name:
```

LABEL=SEA_DISC /media/sdb1 vfat utf8,uid=1000,gid=100,umask=027 0 0

```

---

### Post by PaulM1985 on 2008-07-05
It works!

Thanks very much.

If I changed the /dev/sdb1 to LABEL=SEA_DISC in the fstab file as you mentioned below, would that mean that those permissions would be assigned to the hard disk, no matter which USB socket it is plugged into?

---

### Post by drs305 on 2008-07-05
> **PaulM1985 said:**
> It works!

Thanks very much.

If I changed the /dev/sdb1 to LABEL=SEA_DISC in the fstab file as you mentioned below, would that mean that those permissions would be assigned to the hard disk, no matter which USB socket it is plugged into?

Using a UUID or label to identify a disk/partition is probably a good idea. The sdbX designation is dynamic so the drive/partition isn't specifically tied to any 'sdb' identifier. If you start adding other usb drives it could change, and some updates in the past have changed the standard designations as well (from hda to sda, etc). A label or UUID identifier won't normally change (unless reformatted) and is always tied to the drive/partition, and using them makes fstab a little more 'stable' - for lack of a better term.

This doesn't just apply to USB drives. Many would recommend you edit your fstab to replace your other 'sdXX' designations as well. To do that, as an example, you would change:
```
/dev/sda5 /media/sda5 ext3 defaults 0 0 
```
to:
```

# /dev/sda5
UUID=26a9e71d-486d-48d4-9d49-3d0ab08dece6 /media/sda5 ext3 defaults 0 0 
```
Adding the comment isn't necessary but helps identify the drive when viewing/editing fstab, especially when the mount point doesn't reflect the partition.

There are lots of ways to do things in linux. :)

---

### Post by chrisccoulson on 2008-07-05
If it is an external drive, you shouldn't need an entry in your fstab for it at all. If you remove the /dev/sdb1 entry from your fstab, it should be automatically mounted when you connect it. The user who mounted it will get read-write permissions. If this doesn't happen automatically, then it's a bug or you have some other problem.

You don't need fstab entries to mount external volumes.

Also, your fstab has some redundant entries (highlighted in red), which you should probably remove. The line for your internal NTFS volume could also identify the volume using it's UUID. I've made the change for you (highlighted green)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=26a9e71d-486d-48d4-9d49-3d0ab08dece6 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
UUID=72f1dc91-2a75-40a9-ac55-23137138f148 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
[COLOR="Red"]/dev/sda5 /media/sda5 ext3 defaults 0 0[/COLOR]
[COLOR="Red"]/dev/sda6 /media/sda6 swap defaults 0 0[/COLOR]
[COLOR="Green"]/dev/sda1 
UUID=723862DD38629FB9 /media/sda1 ntfs defaults 0 0[/COLOR]
```

ALso, you are using the old read-only NTFS driver for your NTFS partition. If you want read-write support, you can use the ntfs-3g driver. An example use of this driver to give read-write access to all members of the plugdev group would be:
```
UUID=723862DD38629FB9 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8,uid=0,gid=46,umask=0002 0 0
```

---

