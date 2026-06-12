---
title: "Copying folders"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Karakh on 2008-06-22
OK, this is probably the n00biest question on these boards.

I can copy files from my smb hdd to my second ide hdd, but it wont let me copy folders. I assume that I need to change my permissions but I have no idea where to start.

---

### Post by spiderbatdad on 2008-06-22
You can view the permissions of folder from within the directory containing the folders with the command ls -l, the same way you can view the permissions of individual files inside folders.

Folders and files names containing space require escaping or try quotations around the folder/file names. Use cp -R to copy the folders recursively.

---

### Post by rockerphil on 2008-06-22
i'd personally just log in as root so that i've got unrestricted access if it's really a problem. by default the root password isn't set in Ubuntu, so you can only be granted 15 minutes of root access using the sudo command, so to set your root user password type this in terminal


sudo passwd

it'll ask you for your sudo password, then for the new UNIX password, then verification of the new password. the passwords won't show up as you type them, it's normal. but once the new password is set you can simply log out of your normal account then log in with the user name "root" and the password you set. hope this helps

---

### Post by spiderbatdad on 2008-06-22
> **rockerphil said:**
> i'd personally just log in as root so that i've got unrestricted access if it's really a problem. by default the root password isn't set in Ubuntu, so you can only be granted 15 minutes of root access using the sudo command, so to set your root user password type this in terminal


sudo passwd

it'll ask you for your sudo password, then for the new UNIX password, then verification of the new password. the passwords won't show up as you type them, it's normal. but once the new password is set you can simply log out of your normal account then log in with the user name "root" and the password you set. hope this helps

This is not recommended and has nothing to do with the questions of the op...which is how to copy files. Also, sudo is perfectly effective for root access. Having a root password will not give you any greater control over the filesystem.

---

### Post by Karakh on 2008-06-22
Thanks for the info guys.

I can copy them in the terminal just fine, but I really dont want to have to use the terminal every time (I have to copy files/folders literally 100s of times a day) and I dont like the idea of logging in as root.

Is there no way to just give myself access privileges to copy folders from the gui?

---

### Post by spiderbatdad on 2008-06-22
```
gksu nautilus
```
Be careful...you can break your system by moving or altering the wrong files.

---

### Post by Karakh on 2008-06-22
Yeah, I've been using "gksu nautilus", but its more of a work around than an actual solution, and for some reason, it gives random network errors.

I just want to be able to drag and drop folders from one location to another without being root/su, is that so much to ask?

/sheds a single manly tear :(

---

### Post by bodhi.zazen on 2008-06-22
> **rockerphil said:**
> i'd personally just log in as root so that i've got unrestricted access if it's really a problem. by default the root password isn't set in Ubuntu, so you can only be granted 15 minutes of root access using the sudo command, so to set your root user password type this in terminal


sudo passwd

it'll ask you for your sudo password, then for the new UNIX password, then verification of the new password. the passwords won't show up as you type them, it's normal. but once the new password is set you can simply log out of your normal account then log in with the user name "root" and the password you set. hope this helps

Please do not post information on enabling the root account, especially to new users, without appropriate information.

Appropriate information, IMO, includes at least (although I am sure other mods could add to the list):


[LIST=1]
[*]How to use sudo and gksu.
[*]Permissions.
[*]The risks of enabling the root account and circumventing linux permissions.
[*]How to re-lock the root account.
[/LIST]


The "proper" way to obtain root access is to either :


[LIST=1]
[*]sudo -i
[*]for graphical applications use gksu (kdesu on Kubuntu).
[*]Boot to recovery mode.
[/LIST]


To un-set a root password :

```
sudo passwd root -l
```There are times when it is indeed necessary to set a root password, but they are rare.

While you are free to run your box the way you wish, enabling the root account is in general felt to be bad advice to new users and is discouraged on these forums.

[New forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by bodhi.zazen on 2008-06-22
> **Karakh said:**
> Yeah, I've been using "gksu nautilus", but its more of a work around than an actual solution, and for some reason, it gives random network errors.

I just want to be able to drag and drop folders from one location to another without being root/su, is that so much to ask?

/sheds a single manly tear :(

Setting permissions depends on the file system.

FAT/NTFS are set at the time of mounting.

Linux native file systems use chown and chmod.

Networked shares , again depend on protocol, (samba/nfs).

Can you provide more information ?

---

### Post by Karakh on 2008-06-22
> **bodhi.zazen said:**
> Setting permissions depends on the file system.

FAT/NTFS are set at the time of mounting.

Linux native file systems use chown and chmod.

Networked shares , again depend on protocol, (samba/nfs).

Can you provide more information ?


Im not sure what info you need but heres what I got:

2nd IDE drive - NTFS - /dev/sda (yes its "jumpered" as master)
Network HDD - FAT32/16 - at smb://shared/main

and I need complete access to modify files/folders within/between these drives within the gui, without being root/su.

I can create/modify files/folders within both of the drives, and can copy files between the two, however I cannot copy folders.

---

### Post by bodhi.zazen on 2008-06-22
What is you mount point for your ntfs drive ? /dev/sda refers to the raw partition.

What are the permissions of your mount points ?

ls -l /mount/point

What is this network error mess of which you speak ?

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Karakh on 2008-06-22
> **bodhi.zazen said:**
> What is you mount point for your ntfs drive ? /dev/sda refers to the raw partition.

What are the permissions of your mount points ?

ls -l /mount/point

What is this network error mess of which you speak ?

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)

/media/disk I think

for "ls -l /media/disk" I get :

-rwxrwxrwx 1 root root 0 2008-06-22 15:18 testFile
drwxrwxrwx 1 root root 0 2008-06-22 15:18 testFolder

---

### Post by bodhi.zazen on 2008-06-22
The problem then is the partition is mounted as root.

To change this :

```
sudo umount /media/disk
sudo mount -t ntfs-3g /dev/sda1 /media/disk -o uid=1000,gid=100,dmask=027,fmask=137,nls=utf8
```You can user dmask=000,fmask=111 for more relaxed permissions.

If you want to make this change perm. you need to edit fstab.

```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```Change to line to this:

```
UUID=xxx.yyy.zzz /media/disk ntfs-3g uid=1000,gid=100,dmask=027,fmask=137,nls=utf8 0 0
```Do not change the numbers after UUID
change the locale as needed if you are not in the US.

---

### Post by Karakh on 2008-06-22
sorry for being an idiot but which line do I change?

Fstab contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a44a9679-3a72-4cd2-8250-d60dd44e0ef8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=1546e11b-add0-42c4-b192-e2ccc4de7d46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by bodhi.zazen on 2008-06-22
Ah, looks like you need to add a line.

List your partitions by UUID with :

```
sudo blkid
```

use that uuid in UUID=xxx.yyy.zzz

---

### Post by Karakh on 2008-06-22
OK, from "sudo blkid" I get:

/dev/sda1: UUID="7D0D2B986ED7C143" TYPE="ntfs" 
/dev/sdb1: UUID="a44a9679-3a72-4cd2-8250-d60dd44e0ef8" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="1546e11b-add0-42c4-b192-e2ccc4de7d46" 

So I should add:
"UUID=7D0D2B986ED7C143 /media/disk ntfs-3g uid=1000,gid=100,dmask=027,fmask=137,nls=utf8 0 0"
to fstab?

---

### Post by bodhi.zazen on 2008-06-22
that line looks good.

```
UUID=7D0D2B986ED7C143 /media/disk ntfs-3g uid=1000,gid=100,dmask=027,fmask=137,nls=utf8 0 0
```

---

### Post by Karakh on 2008-06-22
Fantastic, I can now copy folders on my 2nd hdd, thanks alot.

Now I gotta get my SMB hdd doing the same.

---

### Post by bodhi.zazen on 2008-06-22
I advise you start a new thread re: smb .

You might also want to look here :

[uwiki]ComprehensiveSambaGuide[/uwiki]

[uhelp]community/SettingUpSamba[/uhelp]

---

