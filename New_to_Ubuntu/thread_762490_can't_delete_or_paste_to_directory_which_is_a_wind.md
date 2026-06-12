---
title: "can't delete or paste to directory which is a windows partition!"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Santooka on 2008-04-22
well i have this problem that whenever i boot and logon to my ubuntu , there's this partition that i have fat_files_2 , it allows me to paste and delete files and folders at beginning of the session , but after some few minutes it freezes these options , and i don't have a clue why it does that....
i mean i have the root permissions and everything , but i dunno y it freezes the writing permission.
and i dunno if it's only on this folder (partition) or is it on other ones too.

---

### Post by billgoldberg on 2008-04-22
> **Santooka said:**
> well i have this problem that whenever i boot and logon to my ubuntu , there's this partition that i have fat_files_2 , it allows me to paste and delete files and folders at beginning of the session , but after some few minutes it freezes these options , and i don't have a clue why it does that....
i mean i have the root permissions and everything , but i dunno y it freezes the writing permission.
and i dunno if it's only on this folder (partition) or is it on other ones too.

What do you mean you have the root permissions?

Press "alt+f2" then enter "gksudo nautilus" then there should be no problems to copy/paste.

---

### Post by Santooka on 2008-04-22
well i tried that too b4 and it didn't work neither.

---

### Post by billgoldberg on 2008-04-22
If those files are on a windows partition, the problem could be that windows wasn't shut down properly.

It it isn't, I don't know what the problem is.

---

### Post by Santooka on 2008-04-22
the windows was shutdown properly 5 minutes ago and i tried to delete something and it was deleteed, but 5 minutes later i tried to delete another thing , there was no action done at all
from nautilus the list doesn't show neither cut nor move to trash
i tried to use the terminal and i tried to copy the file from its location to another directory and it told me that it's a read only folder that cannot be messed with.

---

### Post by T-Virus on 2008-04-22
Maybe your drivers allows read-only for NTFS partitions? Try ntfs-3g drivers.

---

### Post by PmDematagoda on 2008-04-22
Can you post the output of:-
```
cat /etc/mtab
```

---

### Post by Santooka on 2008-04-22
but that is a fat32 partition not a ntfs partition

---

### Post by Santooka on 2008-04-22
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda5 /fat_files vfat rw,iocharset=utf8,umask=000 0 0
/dev/sda6 /fat_files_2 vfat rw,iocharset=utf8,umask=000 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
/dev/sdc1 /media/DISK2PART1 vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0
/dev/sda7 /media/New\040Volume fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

---

### Post by PmDematagoda on 2008-04-22
Do the other FAT partitions other than fat_files_2 work properly?

---

### Post by Santooka on 2008-04-22
yeah they do

---

### Post by PmDematagoda on 2008-04-22
Ok, now check the partition for errors:-
1) Unmount the partition:-
```
sudo umount /dev/sda6
```

2) Run fsck on it:-
```
sudo fsck -t vfat -r /dev/sda6
```

Post any errors from the fsck check, keep in mind that while the error messages maybe there, the fsck check may still not be finished.

---

### Post by Santooka on 2008-04-22
master@Fady:~$ sudo fsck -t vfat -r /dev/sda6
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
No FSINFO sector
1) Create one
2) Do without FSINFO
? 1
Reserved field in VFAT long filename slot is not 0 (but 0xbb).
1: Fix.
2: Leave it.
? 


what shall i do ?

---

### Post by PmDematagoda on 2008-04-22
> **Santooka said:**
> master@Fady:~$ sudo fsck -t vfat -r /dev/sda6
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
No FSINFO sector
1) Create one
2) Do without FSINFO
? 1
Reserved field in VFAT long filename slot is not 0 (but 0xbb).
1: Fix.
2: Leave it.
? 


what shall i do ?

Hmm, really saying, I am not entirely knowledgeable about the errors you are getting, perhaps you aught to wait for someone who does know what the errors are and what you should do. While I did do some searching around, the particular error you are having does not have that much of a description except for the FSINFO sector error.

---

### Post by Santooka on 2008-04-22
well i performed the fsck and remounted and it is working fine, but i ll wait and c if it will crash again or not

anyways thanx a million for the help :D

---

### Post by Santooka on 2008-04-22
ok i found out that i have to remount it every time it crashes, cuz it did crash right now
so i wrote sudo mount -a and it worked again properly 
is there any chance to fix this?

---

### Post by PmDematagoda on 2008-04-22
Post the output of:-
```
dmesg | tail -25
```

---

### Post by Santooka on 2008-04-22
> master@Fady:~$ dmesg | tail -25
[   60.912566] ACPI: Power Button (FF) [PWRF]
[   60.912625] input: Power Button (CM) as /class/input/input5
[   60.912648] ACPI: Power Button (CM) [PWRB]
[   63.029673] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   65.254032] Failure registering capabilities with primary security module.
[   65.572465] ppdev: user-space parallel port driver
[   66.123689] audit(1208855617.802:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5116 profile="/usr/sbin/cupsd"
[   66.331019] apm: BIOS not found.
[   67.049669] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   67.049686] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   67.049717] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   68.926651] Bluetooth: Core ver 2.11
[   68.926987] NET: Registered protocol family 31
[   68.926994] Bluetooth: HCI device and connection manager initialized
[   68.927001] Bluetooth: HCI socket layer initialized
[   69.029866] Bluetooth: L2CAP ver 2.8
[   69.029874] Bluetooth: L2CAP socket layer initialized
[   69.135237] Bluetooth: RFCOMM socket layer initialized
[   69.135656] Bluetooth: RFCOMM TTY layer initialized
[   69.135664] Bluetooth: RFCOMM ver 1.8
[   74.140446] NET: Registered protocol family 17
[   77.238440] NET: Registered protocol family 10
[   77.239022] lo: Disabled Privacy Extensions
[   87.383871] eth0: no IPv6 routers present
[ 4494.945965] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


there u go

---

### Post by Santooka on 2008-04-22
so?
no answer?:confused:

---

