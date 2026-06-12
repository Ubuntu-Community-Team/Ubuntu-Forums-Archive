---
title: "dual boot: W7 partition not recognized"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by cecisammet on 2012-05-17
Hi everyone! 
I was using Ubuntu 10.04 LTS with WinXP, and a few months ago I had to reinstall windows and I changed XP for W7 (I'm not the only user so I cannot migrate the only PC due to work issues) 
I recovered successfuly the grub after w7 installation, but I have a problem when Ubuntu starts: appears a message saying something like "dev/sda1 is not recognized press s to continue or m to recover manually".
I have a SATA HD with 4 partitions: sda1 and sda2 for W7: 21 GB; sda2 for data: 458 GB, and sda4 for Ubuntu: 21 GB. 
Is there any way to mount this partition, or recognize it and not get this message anymore?

Thanks in advance.

---

### Post by wilee-nilee on 2012-05-17
Post the out put of this command.

```
sudo blkid
```And this one as well.

```
cat /etc/fstab
```You might also try running this and seeing it this still happens with a reboot.

```
sudo update-grub
```

---

### Post by cecisammet on 2012-05-19
I get this:
```

ceci@ceci-desktop:~$ sudo blkid
[sudo] password for ceci: 
/dev/sda1: LABEL="Reservado para el sistema" UUID="F680206880203193" TYPE="ntfs" 
/dev/sda2: UUID="AEB024EFB024BFA7" TYPE="ntfs" 
/dev/sda3: LABEL="Datos" UUID="4CCC548CCC5471E6" TYPE="ntfs" 
/dev/sda4: UUID="bfceca26-767a-4aec-b783-3630909d8d39" SEC_TYPE="ext2" TYPE="ext3" 
ceci@ceci-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext3    errors=remount-ro 0       1
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=FAA0A1E7A0A1AA99 /media/sda1 ntfs-3g users 0 0
UUID=4CCC548CCC5471E6 /media/sda2 ntfs-3g users 0 0
```

And it still happens.

---

### Post by Lisiano on 2012-05-19
Replace FAA0A1E7A0A1AA99 with AEB024EFB024BFA7 in /etc/fstab
To do that, type ```
gksudo gedit /etc/fstab
```

It should look like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext3    errors=remount-ro 0       1
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=AEB024EFB024BFA7 /media/sda1 ntfs-3g users 0 0
UUID=4CCC548CCC5471E6 /media/sda2 ntfs-3g users 0 0
```

---

### Post by Miljet on 2012-05-19
> Replace FAA0A1E7A0A1AA99 with AEB024EFB024BFA7 in /etc/fstab
Maybe I am missing something here, but why would you replace the incorrect UUID of sda1 with the UUID of sda2? If you look again, you will notice that the UUID of both sda1 and sda2 are incorrect in /etc/fstab.

Then again, why would you even mount sda1 or sda2 at startup when data is evidently kept in sda3? Seems to me it would make more sense to auto mount sda3.  

On second look, it appears that sda3 is being mounted, but it is mounted at /media/sda2.

---

### Post by Mark Phelps on 2012-05-20
Don't mount or access sda1 from inside Ubuntu.  It's marked system reserved and if you do anything to it, you risk not being able to boot MS Windows again.  Besides, there's noting in there that you need to access from Ubuntu.

IF sda2 is your Win7 OS partition, the same caution applies there.

You should only be mounting shared NTFS data partitions.

---

### Post by Lisiano on 2012-05-20
> **Miljet said:**
> Maybe I am missing something here, but why would you replace the incorrect UUID of sda1 with the UUID of sda2? If you look again, you will notice that the UUID of both sda1 and sda2 are incorrect in /etc/fstab.

Then again, why would you even mount sda1 or sda2 at startup when data is evidently kept in sda3? Seems to me it would make more sense to auto mount sda3.  

On second look, it appears that sda3 is being mounted, but it is mounted at /media/sda2.
> **Mark Phelps said:**
> Don't mount or access sda1 from inside Ubuntu.  It's marked system reserved and if you do anything to it, you risk not being able to boot MS Windows again.  Besides, there's noting in there that you need to access from Ubuntu.

IF sda2 is your Win7 OS partition, the same caution applies there.

You should only be mounting shared NTFS data partitions.


The mount points set in fstab are arbitrary and if you read the OPs post correctly, you would've noticed he said he reinstalled Windows, thus his old sda1, which had XP was deleted and replaced by a new partition containing Win7, but since Win7 and Vista are ... Khem, weird systems, they create a hidden partition at the beginning of free space, thus his sda1 got shifted downward and became sda2, sda2 became sda3 and his Linux partition became sda4.

The OP didn't want to mount the new sda1, he wanted to mount what was his sda1, which is sda2 now.

Anyway. To make other people less confused, I suggest the OP changes the names from /media/sda1 to /media/Windows and /media/sda2 to /media/Datos

---

### Post by cecisammet on 2012-05-20
Lisiano you are right, but I don't know how to do that. I see the menú like this:         [IMG]http://img594.imageshack.us/img594/7796/pantallazojp.png[/IMG]       Where: floppy0 (my pc has no diskette unit), sda1, and the first sda2  are not mounted, then the second sda2 is the &quot;Datos&quot; or data partition. Is safe the rename? I won't lose anything?      By the way I'm she :p.

---

### Post by Miljet on 2012-05-20
> The OP didn't want to mount the new sda1, he wanted to mount what was his sda1, which is sda2 now.

And once again, as both Mark Phelps and I have pointed out, the OP doesn't need to be mounting the Windows partition through /etc/fstab, no matter what you want to call it. He only needs to be mounting the data partition, whether you call it sda3 or Datos.

---

### Post by Lisiano on 2012-05-20
Okay, open a terminal (Ctrl+Alt+T) and type the following
```
gksudo gedit /etc/fstab
```
Then replace the file with this
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=bfceca26-767a-4aec-b783-3630909d8d39 / ext3 errors=remount-ro 0 1
UUID=4CCC548CCC5471E6 /media/Datos ntfs-3g users 0 0
```
I'll explain what I changed, I removed the Windows mount, renamed where your Datos are mounted to /media/Datos, changed how Root is mounted to prevent any errors in the future and removed the floppy mount as I understand you don't have one in your system, nor will probably have any use for one in our day.

And don't worry, you will not lose anything. Renaming the mount point is the same as saying your favourite cup is now called Cuppy instead of Cupster.

---

### Post by cecisammet on 2012-05-26
Thanks!! It worked perfectly.

---

