---
title: "ubuntu (deja dup) backup failed with an unknown error"
date: 2018-06-19
forum: New to Ubuntu
---

### Post by torbentf on 2018-06-19
Hi,
I got the above message when I tried to backup using deja dup. I have a backup directory (/media/5c41e64a-e4e6-4011-a789-78f495014759/torben) that I created on an external disk (Toshiba). It has all permissions (!). I have searched on the net on the error message but only found something about duplicity and I have checked that I have the latest version of that.
The error message ends with:

self.remote_file.make_directory_with_parents(None)  Error: g-io-error-quark: Error creating directory /media/torben/5c41e64a-e4e6-4011-a789-78f495014759/torben: Permission denied (14)

But, as I said, I already created that directory with all permissions.

Can anyone help?
best regards
torben

---

### Post by deadflowr on 2018-06-19
The directories are different
you created
/media/5c41e64a-e4e6-4011-a789-78f495014759/torben
but the error is for where it probably thinks it should be mounted
at
/media/**torben**/5c41e64a-e4e6-4011-a789-78f495014759/torben

I think it's erring because the location it wants to mount at cannot be mounted at because it's already mounted elsewhere.

---

### Post by torbentf on 2018-06-20
Hi deadfkowr,

 Apparently it is now backing up in /media/5c41e64a-e4e6-4011-a789-78f495014759/torben because there are 3 backups (ordered by me). I wanted to delete them to start from scratch:
 
 
 sudo duplicity remove-older-than 2018-06-21 file://media/5c41e64a-e4e6-4011-a789-78f495014759/torben --force
 gpg: WARNING: unsafe ownership on homedir '/home/torben/.gnupg'
 Local and Remote metadata are synchronized, no sync needed.
 Last full backup date: none
 No old backup sets found, nothing deleted.
 
 
 I have tried:
 torben@torben-Aspire-E5-773G:~$ sudo rm -rf  /media/5c41e64a-e4e6-4011-a789-78f495014759/torben
 torben@torben-Aspire-E5-773G:~$ sudo ls /media/5c41e64a-e4e6-4011-a789-78f495014759/torben
 ls: cannot access '/media/5c41e64a-e4e6-4011-a789-78f495014759/torben': No such file or directory
 
 
 I can still see all the files &#8211; they are there. I cannot right-click them and delete them &#8211; nothing happens if I do right-click them
 
 
 I am confused &#8211; can you help?
 
 
 Torben
 
 
 PS! I am new to Ubuntu

---

### Post by deadflowr on 2018-06-20
What does
```
mount
```
show?

---

### Post by Geoffrey_Arndt on 2018-06-20
What file system does the external media have?   Simplest is just to format it using fat32 (no permissions issue then).

---

### Post by torbentf on 2018-06-21
Hi,
 
 
 I have tried to unmount and mount the external hard disk &#8211; no change.
 
 
 When I look in the file explorer I see two files under the external hard disk:
 
 
 torben
 torben-Aspire-E5-773G
 
 
 When I doppelt-click torben I see my backups. When I doppelt-click orben-Aspire-E5-773G it is empty.
 
 
 When I look up in the terminal I get:
 
 
 torben@torben-Aspire-E5-773G:~$ ls /media
 5c41e64a-e4e6-4011-a789-78f495014759  torben
 torben@torben-Aspire-E5-773G:~$ 
 
 
 There are apparently two files in media:
 
 
 torben@torben-Aspire-E5-773G:~$ ls /media/5c41e64a-e4e6-4011-a789-78f495014759
 [EMAIL="torben@torben-Aspire-E5-773G"]torben@torben-Aspire-E5-773G[/EMAIL]:~$
 
 
 torben@torben-Aspire-E5-773G:~$ ls /media/torben
 5c41e64a-e4e6-4011-a789-78f495014759
 torben@torben-Aspire-E5-773G:~$ 
 
 
 It looks as if the external hard disk is completely screwed up.
 
 
 torben

---

### Post by deadflowr on 2018-06-21
But what does mount show?

---

### Post by torbentf on 2018-06-22
Hi deadflowr and Geoffrey_Arndt, 
 
 I unmounted and mounted in the file explorer.
 
 
 I did it in terminal:
 
 
 t```
orben@torben-Aspire-E5-773G:~$ sudo mount /media/torben/5c41e64a-e4e6-4011-a789-78f495014759
 mount: /media/torben/5c41e64a-e4e6-4011-a789-78f495014759: can't find in /etc/fstab.
 
 
 torben@torben-Aspire-E5-773G:~$ sudo mount /media/5c41e64a-e4e6-4011-a789-78f495014759
 mount: /media/5c41e64a-e4e6-4011-a789-78f495014759: can't find in /etc/fstab.
 
 
```
 Fstab contains:
 
 
```
 torben@torben-Aspire-E5-773G:~$ cat /etc/fstab
 # /etc/fstab: static file system information.
 #
 # Use 'blkid' to print the universally unique identifier for a
 # device; this may be used with UUID= as a more robust way to name devices
 # that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 # / was on /dev/sda2 during installation
 UUID=b3f00031-63d2-4c7a-9356-df0c6d2c0361 /               ext4    errors=remount-ro 0       1
 # /boot/efi was on /dev/sda1 during installation
 UUID=5015-3C0F  /boot/efi       vfat    umask=0077      0       1
 /swapfile                                 none            swap    sw              0       0
```
 
 
 This morning I tried to look it up:
 
 
```
 torben@torben-Aspire-E5-773G:~$ ls /media/5c41e64a-e4e6-4011-a789-78f495014759
 torben@torben-Aspire-E5-773G:~$ ls /media/torben
 5c41e64a-e4e6-4011-a789-78f495014759
 
```
 
 I installed gparted. Gparted in the terminal gave:
 
 
```
 Unit -.mount does not exist, proceeding anyway.
 Gtk-Message: 20:31:15.309: Failed to load module "canberra-gtk-module"
 ======================
 libparted : 3.2
 ======================
 
```
 
 Scanning all devices I got:
 
 
```
 /dev/sda1 EFI System Partition fat32
 */*dev*/*sda2                                    ext4
```
 
 
 It cant see the external hard disk so I cant reformat.
 
 
 torben

---

### Post by vanadium on 2018-06-22
Do not randomly shoot around with sudo commands. deadflowr requested you to post the output of the command "mount" to verify what is mounted where. I would suggest to also provide the output of "lsblk -f" as this also shows the file system used on the drives. To check current permissions of the mount point of the drive, use the command ls with option -l, e.g.  
```

ls -l ls /media/5c41e64a-e4e6-4011-a789-78f495014759

```
where the last part should be substituted by the mount point you want to check (the latter being provided by the lsblk command).

Anyway, the error probably is in the backup path you provide to duplicity. Since quite a few versions of Ubuntu, mount points are under /media/$USER rather than directly under /media

---

### Post by torbentf on 2018-06-22
Hi vanadium,
I finally got it right - thank you very much for your and everybody else's help.
best regards
torben

---

### Post by oldrocker99 on 2018-06-22
Grsync is my go-to for backups, and it works beautifully. Aside from its spurious time left counter, it's perfect for my purposes, and maybe yours as well.

---

