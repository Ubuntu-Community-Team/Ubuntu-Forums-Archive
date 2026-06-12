---
title: "[SOLVED] External USB Harddrive probloems"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by alnilamski on 2008-06-25
Hey all,

I'm using Dapper Drake (6.06), and I have an external usb harddrive that isn't mounting.

I do believe it's supposed to auto-mount and show up on the desktop, and that happens just fine for flash drives and the like, but this drive won't do it.

I tried to mount it, both by going to Places>Computer, and with:
```
sudo mount /dev/sdc1 /media/sdc1
```

It mounts, and then when I try to explore it, it says I don't have the permissions to access it. I've looked through other threads on this, and I'm a little confused: I only have one account on this boot. Why would it ever think I'm not root? Under "Accounts," it certainly says I have all permissions. So I'm pretty confused. I can't even explore this drive in terminal with my sudo password in. I also tried the command "ch___ 777 /media/sdc1" (I forget what the whole command was, I saw it in another thread) that changes permissions, and that didn't help.
Help?

---

### Post by alnilamski on 2008-06-26
Update:
I found out (the noob I am) that simply "su" in the terminal changes user to the superuser. Before, I had just known about preceding a command with sudo.
When I do that, and type the password to the ONLY account on the system (the same password I type for sudo and it works), it says "Authentication failed. Sorry."
Weird?

---

### Post by dr0ff0 on 2008-06-30
I found the same - you cannot use the su to change to the root user account. However, you *can* do it by using sudo bash:

garry@fleegle:~/src/java/projects$ su
Password: 
su: Authentication failure
garry@fleegle:~/src/java/projects$ **sudo bash**
[sudo] password for garry: 
root@fleegle:~/src/java/projects# id
[COLOR="Red"]uid=0(root) gid=0(root) groups=0(root)[/COLOR]
root@fleegle:~/src/java/projects# 

Not sure if this is a security loophole or not, though.

---

### Post by Rocket2DMn on 2008-06-30
su switches to the root user account which is disabled by default in Ubuntu.  The OP has enabled it manually so is able to use su.  If you want a persisting "root" shell without enabling the root account, you can use
```
sudo -s
```
It is not recommended that you do this in case you get sloppy (which if you do it enough, you will).  Even if you do that, you should not enable the root account.

---

### Post by cariboo on 2008-06-30
The only reason you want to use su is to chabe to another user, if you have 2 users you can use su to change to the other user eg

```
user1@computer~$su user2
password:
user2@computer~$
```

JIm

---

### Post by smo0th on 2008-06-30
do as Rocket2DMn advices, type ```
sudo -s
``` in a terminal, you should get root shell, now type 
```
umount /media/sdc1
mount /dev/sdc1 /media/sdc1
ls -l /media/sdc1
```
and paste the output to see what you get :)

---

### Post by vanadium on 2008-06-30
You should not be working with a root user command prompt at all. If you want to issue a command with root privileges, just precede it with sudo.

That said, your drive should indeed automount (although I am not sure anymore for Dapper since I never knew that version). Usually, an USB drive that does not automount is an indication that the file system needs to be checked. I advice to check the file system, which will assure you that the file system is healthy.

To just check it without repair, unmount it first, then run the filecheck:

```

sudo fsck /dev/sdc1

```

Post both the command and its output here.

---

### Post by alnilamski on 2008-07-01
**smo0th**:
Your advice has worked! Thanks for that. But as others have pointed out, it might be a bad idea to be in the root account every time I want to access this hard drive. But your advice yielded this (except I didn't do the umount part because it wasn't mounted yet this time).

```
billy@herbert:~$ sudo -s
Password:
root@herbert:~# mount /dev/sdc1 /media/sdc1
root@herbert:~# ls -l /media/sdc1
total 1904
dr-x------ 1 root root   4096 2007-12-27 00:08 Bach Complete Works - H?nssler
dr-x------ 1 root root   4096 2008-03-04 21:54 Brian
<<and here it lists the rest of the drive's contents, but I think you get the point>>

```
Note that in the GUI file explorer, I still cannot access /media/sdc1. Only in terminal.

**vanadium**:
I unmounted the drive again after following smo0th's advice, and ran the command you said. Here is the output.
```
root@herbert:~# sudo fsck /dev/sdc1
fsck 1.38 (30-Jun-2005)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdc1

```
I also tried throwing a "-t ntfs" in the command, and the output was the same. It is true that this drive is ntfs, but I have no trouble accessing other ntfs drives.

In fact, this very same drive used to be SATA connected and I had no trouble accessing it. For various reasons, I turned that SATA port back off in the BIOS and switched it to a USB drive. Could it be that Ubuntu is angry that the old SATA drive disappeared? The icon that used to be on the desktop for this drive was gone when I first started up after doing that, so I thought that the system had recognized its removal.

---

### Post by Tatty on 2008-07-01
Sorry I dont have the answer to your last question, but if you are unsure of how root and sudo work then I advise you to read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It should clear up a lot of confusion :)

---

### Post by alnilamski on 2008-07-01
**Tatty**:
That did help a lot with my understanding of superuser/root. Thanks!

Still hoping for some help with the hard drive. Thanks for the help so far, everyone.

---

### Post by smo0th on 2008-07-01
> **alnilamski said:**
> **smo0th**:
Your advice has worked! Thanks for that. But as others have pointed out, it might be a bad idea to be in the root account every time I want to access this hard drive. But your advice yielded this (except I didn't do the umount part because it wasn't mounted yet this time).

```
billy@herbert:~$ sudo -s
Password:
root@herbert:~# mount /dev/sdc1 /media/sdc1
root@herbert:~# ls -l /media/sdc1
total 1904
dr-x------ 1 root root   4096 2007-12-27 00:08 Bach Complete Works - H?nssler
dr-x------ 1 root root   4096 2008-03-04 21:54 Brian
<<and here it lists the rest of the drive's contents, but I think you get the point>>

```
Note that in the GUI file explorer, I still cannot access /media/sdc1. Only in terminal.


good there man, let me just comment about the root mode, it's not good to use it in a daily-common fashion because you may inadvertently and accidentally screw up things, it also is a bad idea if someone else locally or remotely has access to your open session, but anyway, using it for troubleshooting is the painless and effortless way to go, but you should know what you're doing.

Alright, now while you are as root in your happy almighty terminal type:

```
chown -hR <yourusername> /media/sdc1
```

this should change the ownership of the entire drive to your normal user, try to refresh and browse your drive from a normal file browser, if this does not work then you should try:

```
cd /media/sdc1
chmod 777 * -R

```

before doing this be aware that this would change your entire sdc1 partition permissions to be read and written by everyone. You may want to try different chmod permissions, it's up to you, here's a [chmod tutorial]("http://www.analysisandsolutions.com/code/chmod.htm").

---

### Post by alnilamski on 2008-07-02
I tried both chown and chmod, and I read that nice tutorial. It really seems like it should work, and when I execute either chown or chmod it takes a bit and shows a zillion files and directories being changed in the terminal, but then it STILL says permission denied when I try to browse to it, or when I try to access it in another terminal session where I'm not root.
Does this make any sense?

This is what ls -l looks like in sdc1 after I've run chmod 777.
```
root@herbert:/media/sdc1# ls -l
total 1904
dr-x------ 1 root root   4096 2007-12-27 00:08 Bach Complete Works - H?nssler
<<the same for all directories>>
-r-------- 2 root root      0 2007-06-28 16:40 this is a test file.txt
<<the same for all files>>

```

---

### Post by Rocket2DMn on 2008-07-02
If your external drive is NTFS, you can't chown or chmod it, that is only for filesystems with linux filesystems permissions.  Please post
```
sudo fdisk -l
cat /etc/fstab
mount
sudo blkid
```
Have you downloaded ntfs-config?
```
sudo apt-get install ntfs-config
```
Then go to Applications->System Tools->NTFS Configuration Tool and check the box to enable write support.

---

### Post by smo0th on 2008-07-02
or try mounting it with the ntfs-3g directive.

---

### Post by vanadium on 2008-07-03
An external USB should not be included in /etc/fstab. It should mount automatically, although I am not completely sure for a version as Dapper which is getting a bit old. Before proceeding and receiving random advice, you should indeed, with the drive connected, post the output of the commands provided in Rocket2DM's post.

From what you showed already, the file system will be OK, so my suggestion does not further apply. For an ntfs file system, any checking should be done with a Windows system anyway, not with Ubuntu. The error message you obtained was because you do not have ntfsfix installed.

---

### Post by alnilamski on 2008-07-03
Here is the output from Rocket's post.

```
billy@herbert:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       18975   152368492+   7  HPFS/NTFS
/dev/sda3           18976       19452     3831502+  db  CP/M / CTOS / ...

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9872    79296808+   7  HPFS/NTFS
/dev/sdb2            9873       10646     6217155   83  Linux
/dev/sdb3           10647       10908     2104515   82  Linux swap / Solaris
/dev/sdb4           10909       12188    10281600   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
billy@herbert:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb4       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sdc1       /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sdb3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
billy@herbert:~$ mount
/dev/sdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-52-386/volatile type tmpfs (rw)
/dev/sdb4 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda3 on /media/sda3 type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb1 on /media/sdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
billy@herbert:~$ sudo blkid
/dev/sdc1: TYPE="ntfs"
/dev/sda1: UUID="07D5-0616" LABEL="DellUtility" SEC_TYPE="msdos" TYPE="vfat"
/dev/sda2: TYPE="ntfs"
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat"
/dev/sdb1: TYPE="ntfs"
/dev/sdb2: UUID="52ab5b2c-4dbf-40b2-bb88-511ab83417a6" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb3: TYPE="swap"
/dev/sdb4: UUID="6b545c1b-e6b1-46fa-8e7e-b85cc41875cf" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/sda1: UUID="07D5-0616" LABEL="DellUtility" SEC_TYPE="msdos" TYPE="vfat"
/dev/evms/sda2: TYPE="ntfs"
/dev/evms/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat"
/dev/evms/sdb1: TYPE="ntfs"
/dev/evms/sdb2: UUID="52ab5b2c-4dbf-40b2-bb88-511ab83417a6" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/sdb3: TYPE="swap"
/dev/evms/sdb4: UUID="6b545c1b-e6b1-46fa-8e7e-b85cc41875cf" SEC_TYPE="ext2" TYPE="ext3"

```

I have other NTFS drives that are perfectly accessible. As I've said, even this drive was fine back when it was SATA mounted.
Nonetheless, I tried getting ntfs-config. Package not found!
```
billy@herbert:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config

```
It wasn't in Synaptic either, as far as I could tell.

So what is the ntfs-3g directive? Are you saying I should mount it with the type in it, like (not 100% sure on the syntax here)
```
mount -t NTFS /dev/sdc1 /media/sdc1
```?

---

### Post by Rocket2DMn on 2008-07-03
You need to enable the universe and multiverse repositories, go to System->Administration->Software Sources and check the boxes for universe and multiverse.  Close the window and allow it to update, then try to install ntfs-config.
Now, assuming your external drive is /dev/sdc, you should remove the entry from fstab
```
gksudo gedit /etc/fstab
```
and comment out the line
```
/dev/sdc1       /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
```
so that it looks like
```
# /dev/sdc1       /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
```
Save and exit, enable writing to external from ntfs-config, then plug the drive in.

---

### Post by vanadium on 2008-07-03
ntfs write support might not be available for Dapper. Are you sure that "other ntfs drives are perfectly accessible" (i.e. read and write)? I do not see the ntfs-3g driver listed nowhere.

---

### Post by Rocket2DMn on 2008-07-03
Oh, the OP is using Dapper, I'm sorry (I started helping a little later in the thread).  You are absolutely right, Dapper does not have ntfs-3g in the repositories, you have to use third party repos to get it.  Have a look at this wiki help page and have a look at the section for Dapper - [uhelp]community/MountingWindowsPartitions/ThirdPartyNTFS3G[/uhelp]
Please let me know if that works.  I rewrote that wiki page about a week ago, but I kept the pre-existing material for Dapper since I had no way to test it out.  I would appreciate knowing if those directions are still accurate (and those repos are still active).

---

### Post by alnilamski on 2008-07-05
Thank you so much! I got ntfs-config and commented out the sdc1 line in fstab, and before I could even try mounting it, I noticed it was already right there on the desktop! Now it auto-mounts and everything when I turn the drive on.

So this also verifies that the Dapper information on that wiki page works, Rocket2DMn.

And vanadium, you're right; my internal drives weren't writable, so I guess they weren't 'perfectly' accessible.

Thank you all for your help.

---

### Post by smo0th on 2008-07-05
good learning :D

---

### Post by Rocket2DMn on 2008-07-05
> **alnilamski said:**
> Thank you so much! I got ntfs-config and commented out the sdc1 line in fstab, and before I could even try mounting it, I noticed it was already right there on the desktop! Now it auto-mounts and everything when I turn the drive on.

So this also verifies that the Dapper information on that wiki page works, Rocket2DMn.

And vanadium, you're right; my internal drives weren't writable, so I guess they weren't 'perfectly' accessible.

Thank you all for your help.

Groovy, thanks for posting back with that, I appreciate it.

---

