---
title: "re-format FDD"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by czgirb on 2013-03-16
Today I wish to re-format my FDD ... so I go to G-Parted and do the re-format proses.
But **I forget to unmount** the FDD first ... so the process is **failed**.
And now my FDD become **unallocated**.
Since I found no **unmount** with mouse right-click ... so I think the FDD was **unmounted** already. Is it right?
 If YES, what should I do?
If it's NOT, what should I do?
Please guide me

---

### Post by Bashing-om on 2013-03-16
czgirb; Hi !

Most likely the filesystem still holds the device as busy. I assume FDD = Floppy Drive Device ?
Here is one method.
Try this from terminal:
```
umount: /dev/FDD
``` result : device is busy ?
Then:
```
fuser -m /dev/FDD
``` result : /dev/FDD: 3322 (that will be some other process identification number)
Then:
```
kill -9 3322 
``` (substitute your process ID from above)
and now to (un)mount the device:
```
umount /dev/FDD
```[INDENT=2]
I do hope this helps

[/INDENT]

---

### Post by czgirb on 2013-03-16
czgirb@czgirb:~$ umount: /dev/FDD
No command 'umount:' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)
umount:: command not found
czgirb@czgirb:~$ unmount: /dev/FDD
unmount:: command not found
czgirb@czgirb:~$

---

### Post by schragge on 2013-03-16
It's **umount**, not **umount[COLOR=#FF0000]:[/COLOR]**

Also note that you may need root privileges to execute *umount*. But before doing this, please post the output of
```
mount
```
```
sudo blkid -o list -c /dev/null
```

---

### Post by sudodus on 2013-03-16
> **czgirb said:**
> czgirb@czgirb:~$ umount: /dev/FDD
No command 'umount:' found, did you mean:
 

The command is ```
sudo umount /dev/FDD
``` without colon

---

### Post by czgirb on 2013-03-16
> **schragge said:**
> It's **umount**, not **umount[COLOR=#FF0000]:[/COLOR]**

Also note that you may need root privileges to execute *umount*. But before doing this, please post the output of
```
mount
```
```
sudo blkid -o list -c /dev/null
```


czgirb@czgirb:~$ mount
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
/dev/sda4 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/czgirb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=czgirb)
/dev/sdb1 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
czgirb@czgirb:~$ sudo blkid -o list -c /dev/null
[sudo] password for czgirb: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              1a61250f-928d-4a29-b75d-a7cf8198b1b3
/dev/sda2  ntfs    RECOVERY (not mounted)  D2BE3BDFBE3BBAB5
/dev/sda3  swap             <swap>         482233f6-6ff9-4dbb-97c0-8efcf693c4e9
/dev/sda4  ext4             /home          8580d3f9-05cf-4b89-b766-12c0e6f43e91
/dev/sdb1  ntfs    Data     /media/Data    A2C864A8C8647C83
czgirb@czgirb:~$

---

### Post by czgirb on 2013-03-16
> **sudodus said:**
> The command is ```
sudo umount /dev/FDD
``` without colon

czgirb@czgirb:~$ sudo umount /dev/FDD
umount: /dev/FDD: not found
czgirb@czgirb:~$

---

### Post by sudodus on 2013-03-16
It seems you have no floppy, so you should not use FDD

```
/dev/sda1  ext4             /              1a61250f-928d-4a29-b75d-a7cf8198b1b3
/dev/sda2  ntfs    RECOVERY (not mounted)  D2BE3BDFBE3BBAB5
/dev/sda3  swap             <swap>         482233f6-6ff9-4dbb-97c0-8efcf693c4e9
/dev/sda4  ext4             /home          8580d3f9-05cf-4b89-b766-12c0e6f43e91
/dev/sdb1  ntfs    Data     /media/Data    A2C864A8C8647C83
```

/dev/sda1 is your Ubuntu root partition
/dev/sda2 is a recovery partition from a wiped Windows installation
/dev/sda3 is Ubuntu's swap partition
/dev/sda4 is your Ubuntu /home partition
and
/dev/sdb1 is your data partition on a second drive.

***What do you want to do***? To which of the drives? ***Is there a third drive***, that is not seen by the command that wrote the output you posted?

---

### Post by czgirb on 2013-03-16
> **sudodus said:**
> It seems you have no floppy, so you should not use FDD

```
/dev/sda1  ext4             /              1a61250f-928d-4a29-b75d-a7cf8198b1b3
/dev/sda2  ntfs    RECOVERY (not mounted)  D2BE3BDFBE3BBAB5
/dev/sda3  swap             <swap>         482233f6-6ff9-4dbb-97c0-8efcf693c4e9
/dev/sda4  ext4             /home          8580d3f9-05cf-4b89-b766-12c0e6f43e91
/dev/sdb1  ntfs    Data     /media/Data    A2C864A8C8647C83
```

/dev/sda1 is your Ubuntu root partition
/dev/sda2 is a recovery partition from a wiped Windows installation
/dev/sda3 is Ubuntu's swap partition
/dev/sda4 is your Ubuntu /home partition
and
/dev/sdb1 is your data partition on a second drive.

***What do you want to do***? To which of the drives? ***Is there a third drive***, that is not seen by the command that wrote the output you posted?

it was a flashdisk ... as I said, it was been **unallocated** by G-Parted.
So ... now, it was not detected by ubuntu ... and it was not listed.
That's why I do not know what to do
Please help me ...

---

### Post by sudodus on 2013-03-16
OK, it is a flash memory. A flash card, a USB flash pendrive or an SSD sata drive?

Anyway, the system might be confused, so reboot and see if it will find that drive again :-)

---

### Post by czgirb on 2013-03-17
> **sudodus said:**
> OK, it is a flash memory. A flash card, a USB flash pendrive or an SSD sata drive?

Anyway, the system might be confused, so reboot and see if it will find that drive again :-)

Yesterday I plugged the **FDD** to my **XP** computer ... and it's none.
So I open **Disk Management** and found it was there, so I format it to **FAT32** and it works.
So ... the case is **SOLVED**.
[B]Thank you.

HDD=Hard Drive Disk = Harddisk
FDD = Flash Drive Disk = Flashdisk = USB-Pendrive
is the statement above is right?

[/B]How to marked the thread as **SOLVED** thread?
**Thread Tools :** Print / e-Mail / Subscribe
**Display :** Linear / Hybird / Threaded

---

### Post by Paqman on 2013-03-17
> **czgirb said:**
> 
HDD=Hard Drive Disk = Harddisk
FDD = Flash Drive Disk = Flashdisk = USB-Pendrive
is the statement above is right?[/B]

Half right;

HDD = Hard disk drive
FDD = Floppy disk drive. You're about as likely to have one of these in your machine as you are to see a brontosaurus strolling past your window.

---

