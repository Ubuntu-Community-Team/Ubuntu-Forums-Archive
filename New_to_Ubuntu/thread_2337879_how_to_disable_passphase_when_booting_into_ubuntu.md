---
title: "how to disable passphase when booting into ubuntu"
date: 2016-09-22
forum: New to Ubuntu
---

### Post by houmingc on 2016-09-22
```
chew@alvin-UX32VD:~$ sudo fdisk -l
[sudo] password for alvin: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4f359092

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26f2eac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    46905263    23452631+  ee  GPT

Disk /dev/mapper/sdb3_crypt: 23.2 GB, 23218618368 bytes
255 heads, 63 sectors/track, 2822 cylinders, total 45348864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sdb3_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--kylin--vg-root: 19.0 GB, 19025362944 bytes
255 heads, 63 sectors/track, 2313 cylinders, total 37158912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--kylin--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--kylin--vg-swap_1: 4173 MB, 4173332480 bytes
255 heads, 63 sectors/track, 507 cylinders, total 8151040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--kylin--vg-swap_1 doesn't contain a valid partition table
```

---

### Post by TheFu on 2016-09-22
a) don't use fdisk on GPT disks. Use parted or gparted.
b) Please add "code tags" to all command output. Too hard to read otherwise.
c) It isn't clear to me what the disk output has to do with the subject.
d) "passphrase" isn't clear.  Did you encrypt the disk during the install or just want to have the system automatically login to a desktop with your userid?  These are separate, different issues.

Please help us understand clearly the issue.

---

### Post by ajgreeny on 2016-09-22
By the looks of your posted terminal output you are using either LVM or encryption, or perhaps the first means the second is the case.

Tell us in a lot more detail about what you have got on the computer and what exactly you want.  To the best of my knowledge if you have encrypted the disk or partition there is no way to avoid entering a password or passphrase, but I may be wrong about that, and again, we need more info about your wishes.

---

### Post by houmingc on 2016-09-22
I like to have the system automatically login to the desktop. 
I am following ubuntu standard install, don't think i encrypt the disk(SSD).
Is it because when i purchase the laptop the SSD is already encrypted?

I like to disable password prompt upon startup in ubuntu like the link describe below.
[http://askubuntu.com/questions/304964/disable-password-prompt-upon-startup-in-ubuntu-server]("http://askubuntu.com/questions/304964/disable-password-prompt-upon-startup-in-ubuntu-server")

---

### Post by Geoffrey_Arndt on 2016-09-22
The link refer's to a server based ubuntu and it looks like you have a standard desktop install.

Running a system without requiring a user login password is considered to be a security risk in most cases.   That is why that behaviour is not allowed at any company or similar organization.   Just not a smart thing to do.

---

### Post by oldrocker99 on 2016-09-23
You can go to Users and Groups, and where it shows Password: **Asked on login** [change], click on change and you can remove the password being asked for at login. You will have to enter your password later for the keyring anyway. 

You can select automatic straight to the desktop when you install the system (on the page where you enter your name) but you'll still have to enter your password for the keyring. In fact, I don't know of any other way to boot directly to the desktop, besides a new installation.

---

### Post by TheFu on 2016-09-23
The fdisk output implies that encryption is being used, but we need to see the **parted** output to be certain. fdisk doesn't work with GPT disks.   I don't know how to remove whole disk encryption without doing a reinstall.  I'd like to see **lvs**, **vgs**, and **lsblk** output too. Add sudo to those commands, as needed to get output.

*Background:*
OTOH, all portable devices need whole drive encryption as far as I'm concerned.  Had a laptop and a smartphone stolen when traveling.  The laptop had whole drive encryption - it was just a HW loss.  The smart phone didn't, but I'd cleaned sensitive data from it prior to the trip. Thanks to a friend inside a cell company, we traced my stolen phone to central Africa - it was banned from cell networks in all modern countries. For the next few weeks, my contacts got strange phone calls and emails. I'd not deleted those.  I had changed all the passwords within 30 minutes of the theft, however.

Encrypting all storage during the disk warranty period might be smart too. When we return a failed HDD for warranty service, I'd rather not have some tech there being able to review all the files the disk may have stored.  Just sayin'.

---

