---
title: "ownership issues"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by djyoung4 on 2012-10-18
So I have two storage drives which are mounted in /mnt/ but anytime I try and change any of the files I get a permission denied.  How would I change the ownership to my user.  They are both in fat 32 format.

---

### Post by mittwit on 2012-10-18
If the drives show up in the left column of Nautilus, the file browser, you can right click them and select *properties* then *permissions*
Try changing the access permissions here.
If they don't show in the left column you should find them by browsing to the mnt folder.

---

### Post by juancarlospaco on 2012-10-18
Impossible to know without the description on how you mounted it.

BTW ubuntu AUTO-mount on /media/   :)

---

### Post by NikTh on 2012-10-18
Hi , 

Fat32 filesystem does not support permissions by Linux. So if you dynamically connect a Fat32 filesystem you probably will have the problem that you have right now. 

A workaround could be to mount differently the drive. 
If you want to mount permanently see here: 
 [Unsterstand Fstab by ]("http://ubuntuforums.org/showthread.php?t=283131")[bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054")

You can try this 
1) connect the drive and give this command
```
sudo fdisk -l
``` so you can see what is the /dev name of the partition of the drive. We assume now , that is /dev/sdb1. 
If automatically mounted under /media/ , then unmount it first
```
sudo umount /dev/sdb1/
```

Then do 
```
mdkir flash/ 
sudo mount /dev/sdb1 ~/flash/ -o  dmask=000,fmask=111
```and see if you have permissions.

You can try with chown to take ownership from all folders and files.
```
sudo chown username:username -R ~/flash/
```
Where username replace it with yours and hopefully chown will work to get the ownership of all folders and files inside ~/flash/ mount-point.

If you don't want to interfere with such procedures , you can simply open the nautilus file manager as a root 
```
gksudo nautilus
```and you will have write-read access. 

sources:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://askubuntu.com/questions/96923/how-do-i-change-permissions-on-a-fat32-formatted-drive/96929#96929](http://askubuntu.com/questions/96923/how-do-i-change-permissions-on-a-fat32-formatted-drive/96929#96929)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by djyoung4 on 2012-10-18
> **mittwit said:**
> If the drives show up in the left column of Nautilus, the file browser, you can right click them and select *properties* then *permissions*
Try changing the access permissions here.
If they don't show in the left column you should find them by browsing to the mnt folder.
They don't show up in the left side of nautilus but they are in mount because I added them to the fstab
> **juancarlospaco said:**
> Impossible to know without the description on how you mounted it.

BTW ubuntu AUTO-mount on /media/   :)
I added them to the fstab with instructions from [a previous thread]("http://ubuntuforums.org/showthread.php?p=12267987#post12267987").
NikTh, I will try that method when I can get reconnected to the box.  Why is it always when it needs to work it never does

---

### Post by bab1 on 2012-10-19
> **djyoung4 said:**
> They don't show up in the left side of nautilus but they are in mount because I added them to the fstab

I added them to the fstab with instructions from [a previous thread]("http://ubuntuforums.org/showthread.php?p=12267987#post12267987").
NikTh, I will try that method when I can get reconnected to the box.  Why is it always when it needs to work it never doesYou need to  set the ownership at mount time.  Post your entry in /etc/fstab.

---

### Post by djyoung4 on 2012-10-19
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a134e42c-9aa4-41b1-9a90-7a2ea5ded5ad /               ext4    errors=remount-ro 0       1
UUID=F756-FF06 /mnt/Storage1    vfat     defaults         0        2
UUID=4E6C-BB98 /mnt/Storage2    vfat     defaults         0        2
# swap was on /dev/sda5 during installation
UUID=bd495572-5a90-407f-afb0-2aeabb9cd9b9 none            swap    sw              0       0
```
I tried changing the mount points from /mnt/Storage1 and /mnt/Storage2 to /home/Storage1 and /home/Storage2 which I probably should have done in the first place but it did not show up in home

---

### Post by bab1 on 2012-10-19
> **djyoung4 said:**
> 
I tried changing the mount points from /mnt/Storage1 and /mnt/Storage2 to /home/Storage1 and /home/Storage2 which I probably should have done in the first place but it did not show up in home

Where the mounts "show up" is not a function of ownership.  So I'm a little confused here.  Do you want to have permissions rights or see these partitions in your home directory or both?

IF you want the file permissions to be you as owner and group then you would use something like this in the fstab file```
UUID=F756-FF06 /mnt/Storage1    vfat     **defaults,uid=1000,gid=1000**         0        2
UUID=4E6C-BB98 /mnt/Storage2    vfat     **defaults,uid=1000,gid=1000**         0        2
```
This should mount the partition with you (assuming you are the first user configured when installing Ubuntu) as the owner and group owner.

Let us know how it worked out for you.

---

