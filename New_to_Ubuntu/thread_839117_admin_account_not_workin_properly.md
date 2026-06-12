---
title: "admin account not workin properly"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by umarali on 2008-06-24
hi, i recently upgraded from gutsy to hardy n its been running smoothly since just now. i use an admin account n it suddenly started doing weird stuff...i had been downloading something through Ktorrent, it gave an error saying "read-ony file system"...Amarok wouldnt start up....n ive got an "unlock" icon next to all my folders!!! :s
!!!!!!!!
any help will be greatly appreciated.

ps: other accounts (non-admin) working fine!

---

### Post by umarali on 2008-06-24
btw.....i was getting a fsck error at start up....so i typed in fsck in the terminal and got this:
```
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=b80bd76e-3905-412a-a259-e4d01dd3ef15'

```
dunno what it means....but it doesnt look good...i guess! :/

---

### Post by gtdaqua on 2008-06-24
Wat exact 'admin' account were you using? 

The highest-privileged account in linux 'root'. They are never referred as 'admin' accounts.

---

### Post by chrisccoulson on 2008-06-24
The first user belongs to the 'admin' group.

umarali, could you please post the output of the following in a terminal:
```
cat /etc/fstab
sudo blkid
sudo fdisk -l
sudo mount -l
dmesg
```

You might want to attach the output of dmesg as a text file.

Also, do you know which filesystem is reported as being read-only? (What folder is ktorrent saving data too)?

You might have 2 separate problems here. The fsck error is likely to be a stale entry in your fstab, and the read-only filesystem might be caused due to filesystem errors (dmesg may give more of an idea)

Thank you

---

### Post by umarali on 2008-06-25
its saying this for anywhere i try saving something in my profile.....even firefox wont download stuff! my documents, videos, music, desktop....EVERYTHING!!!!
by the way..
this is what i got:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b80bd76e-3905-412a-a259-e4d01dd3ef15 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e8b2ea8d-c65b-4a53-8d0e-1be8f5b07bfe none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```
for "sudo blkid"
i got:
```
/dev/sda1: UUID="b80bd76e-3905-412a-a259-e4d01dd3ef15" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="e8b2ea8d-c65b-4a53-8d0e-1be8f5b07bfe" 

```
n for "sudo fdisk -l":
```

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08a108a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7193    57777741   83  Linux
/dev/sda2            7194        7476     2273197+   5  Extended
/dev/sda5            7194        7476     2273166   82  Linux swap / Solaris

```

n "sudo mount -l"gave:
```
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/umar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=umar)

```

i had problems with the text file for "dmesg" so i copy pasted it on google docs and emaild to u one the address u have given in ur profile.

thank you a million

---

### Post by umarali on 2008-06-30
hello? :/

---

### Post by nowshining on 2008-06-30
u can try to change:

```
 # /dev/hda1
UUID=b80bd76e-3905-412a-a259-e4d01dd3ef15 /               ext3    defaults,errors=remount-ro 0     
```

to

```
 

# /dev/hda1
UUID=b80bd76e-3905-412a-a259-e4d01dd3ef15 /               ext3    defaults,errors=remount-ro,noatime,relatime,auto,rw,dev,exec,suid 0 1

```

u can remove the noatime and relatime if u like - relatime is suppose to be better than the reg. attime and of course better performance wise.


if need be - u may need to go into the livdcd and mount the drive and edit the /etc/fstab file - of which would me in /media/nameoffolderuchosetocreate /etc/fstab

and u need sudo privs to edit it.

---

### Post by chrisccoulson on 2008-06-30
umarali - sorry for the delay in replying. The read-only problem could be due to filesystem errors, which may need to be corrected. If a filesystem gets errors on it, the kernel will remount it read-only to minimise further damage. Your fstab correctly specifies the 'defaults' option, which means it *should* mount read-write unless there are errors. Because you've already seen fsck errors at start-up, I'd be inclined to believe that you have a problem with the filesystem.

Obviously, if the root filesystem has gone read-only, there may not be any useful information in your /var/log/syslog, but have a look anyway as you might spot something useful. What you're looking for is something along the lines of 'Filesystem panic'. If you're unsure of anything in the log, just ask.

With regards to your fsck error - How did you try to run fsck? Did you just type 'fsck' in to a terminal? If so, that error is expected, as e2fsck will not resolve the UUID without root privileges. Nevertheless, this is not the way to run fsck anyway - the partition **must** be unmounted first, else you risk serious breakage.

Do you remember what the fsck errors at startup were? Is there anything in /var/log/fsck/checkfs and /var/log/fsck/checkroot? If you're unsure, just post those files here.

I'd suggest you force a fsck on your disk. To do this, open up a terminal and do the following:
```
sudo touch /forcefsck
sudo reboot
```
This will reboot the system and run fsck at startup. Obviously, if the filesystem has gone read-only at this point, then this will not work, as you will not be able to touch the file 'forcefsck'. In this scenario, you would be better off running fsck from the live CD. If you need to do this, I can provide further assistance. Running fsck from the live CD would enable you to record the terminal output and paste it here.

---

