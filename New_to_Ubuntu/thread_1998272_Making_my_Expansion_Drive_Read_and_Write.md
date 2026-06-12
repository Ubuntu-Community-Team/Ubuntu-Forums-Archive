---
title: "Making my Expansion Drive Read and Write"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Jack Nitro on 2012-06-06
Now, I'm aware that there's about a million and a half threads on this issue already, but all of the ones I've tried either didn't work or were incomprehensible to my tiny brain. 

Anyway, I need to back up my internal Hard drive to this External hard drive. I want to do it as simply as possible, so I'm trying to simply use

```
cp -r /media/OS* /media/Expansion-Drive
```

Easy, right? I was able to get it to start copying to my Linux partition without issue -- obviously, however, the Linux partition doesn't have the necessary ~200GB i need. But when I use the above command...

```
jack@jack-Studio-1735:~$ cp -r /media/OS* /media/Expansion-Drive
cp: cannot create directory `/media/Expansion-Drive/OS': Read-only file system
```

Can someone help me with either a simple solution or baby steps through some more complex Linux magic?

---

### Post by d4m1r on 2012-06-06
Have you tried "sudo cp ...."? That might not solve it either however, in which case you should google or search on here something like "ubuntu external drive permissions". My hunch is that you just need to add write and execute permissions to your (likely) NTFS external HDD.

---

### Post by Jack Nitro on 2012-06-06
Yes it's NTFS, I probably should have mentioned that...

I did try to modify /etc/fstab using gedit, but that doesn't seem to have done anything:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e7b5c6ba-0d33-4071-985f-37594e67d4ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=5a4a688e-43bc-47a8-9b30-c5d6a044f826 none            swap    sw              0       0
UUID=2E30895D30892CC1  /media/Expansion-Drive  ntfs  user,uid=1000,gid=100,dmask=027,fmask=137  0  0
```
UUID=2E30895D30892CC1...0   0 is the line I added.

Also, yes, I've already tried sudo.

---

### Post by idoitprone on 2012-06-06
> **Jack Nitro said:**
> Yes it's NTFS, I probably should have mentioned that...

I did try to modify /etc/fstab using gedit, but that doesn't seem to have done anything:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e7b5c6ba-0d33-4071-985f-37594e67d4ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=5a4a688e-43bc-47a8-9b30-c5d6a044f826 none            swap    sw              0       0
UUID=2E30895D30892CC1  /media/Expansion-Drive  ntfs  user,uid=1000,gid=100,dmask=027,fmask=137  0  0
```UUID=2E30895D30892CC1...0   0 is the line I added.

Also, yes, I've already tried sudo.

next time follow this guide, arch sometimes have better docs than ubuntu
[https://wiki.archlinux.org/index.php/NTFS-3G#Default_settings](https://wiki.archlinux.org/index.php/NTFS-3G#Default_settings)

[https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)

change your fstab
```
UUID=2E30895D30892CC1 /media/Expansion-Drive ntfs defaults  0  0
```your ntfs have to be remounted. NTFS permission are determined on mount and cannot be change thereafter

change your fstab then reboot
or remount it

---

### Post by Jack Nitro on 2012-06-06
> **idoitprone said:**
> next time follow this guide, arch sometimes have better docs than ubuntu
[https://wiki.archlinux.org/index.php/NTFS-3G#Default_settings](https://wiki.archlinux.org/index.php/NTFS-3G#Default_settings)

[https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)

change your fstab
```
UUID=2E30895D30892CC1 /media/Expansion-Drive ntfs defaults  0  0
```your ntfs have to be remounted. NTFS permission are determined on mount and cannot be change thereafter

change your fstab then reboot
or remount it

I tried all of the commands mentioned in the arch article for NTFS (ubuntu didn't seem to recognize it as "ntfs-3g", so I just switched it for "ntfs" in all of the examples). Even after individually 
```
sudo umount /dev/sdb1
```
and then
```
gksudo gedit /etc/fstab
```
and then restarting for each one, NONE of them worked. Every time I ran
```
sudo mount /dev/sdb1
```
I got the warning
```
jack@jack-Studio-1735:~$ sudo mount /dev/sdb1
mount: warning: /media/Expansion-Drive seems to be mounted read-only.

```
And cp -r STILL wouldn't work. Same error as always.

It's been over a week trying to restore this thing. I'm truly at wits end -- Hulk-level frustration building here.

---

### Post by idoitprone on 2012-06-06
> **Jack Nitro said:**
> I tried all of the commands mentioned in the arch article for NTFS (ubuntu didn't seem to recognize it as "ntfs-3g", so I just switched it for "ntfs" in all of the examples). Even after individually 
```
sudo umount /dev/sdb1
```and then
```
gksudo gedit /etc/fstab
```and then restarting for each one, NONE of them worked. Every time I ran
```
sudo mount /dev/sdb1
```I got the warning
```
jack@jack-Studio-1735:~$ sudo mount /dev/sdb1
mount: warning: /media/Expansion-Drive seems to be mounted read-only.

```And cp -r STILL wouldn't work. Same error as always.

It's been over a week trying to restore this thing. I'm truly at wits end -- Hulk-level frustration building here.

did you change your fstab?
then reboot as i asked
[FONT=monospace]
[/FONT]```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5)
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e7b5c6ba-0d33-4071-985f-37594e67d4ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=5a4a688e-43bc-47a8-9b30-c5d6a044f826 none            swap    sw              0       0
UUID=2E30895D30892CC1 /media/Expansion-Drive ntfs defaults  0  0
```this should be your resulting fstab, just changed the last line
if that did not work then i guess try 

```
UUID=2E30895D30892CC1 /media/Expansion-Drive ntfs rw,umask=0000,defaults  0  0
```

here commands to mount

```
sudo umount /dev/sdb1
sudo mkdir /mnt/ntfs
sudo mount -t ntfs /dev/sdb1 /mnt/ntfs
```full guide here
[http://linuxconfig.org/How_to_mount_partition_with_ntfs_file_system_and_read_write_access](http://linuxconfig.org/How_to_mount_partition_with_ntfs_file_system_and_read_write_access)

---

### Post by Jack Nitro on 2012-06-06
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e7b5c6ba-0d33-4071-985f-37594e67d4ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=5a4a688e-43bc-47a8-9b30-c5d6a044f826 none            swap    sw              0       0
UUID=2E30895D30892CC1 /media/Expansion-Drive ntfs defaults  0  0
```

Yep, looks the same.

I'll try your second suggestion. Fingers crossed.

---

### Post by Jack Nitro on 2012-06-06
OK. SERIOUSLY FEEL STUPID NOW.

Turns out that I had the wrong drivers installed. I was supposed to have ntfs-3g installed, didn't even realize that...

Sorry idoitprone for putting you through all of that -- I'll be sure and buy you something nice this christmas ;)

---

### Post by Morbius1 on 2012-06-06
The clue may be here:
> I tried all of the commands mentioned in the arch article for NTFS (ubuntu didn't seem to recognize it as "ntfs-3g", so I just switched it for "ntfs" in all of the examples). 
There is a symbolic link between ntfs and ntfs-3g in Ubuntu. When you specify "ntfs" in fstab it automatically links it to the ntfs-3g driver. If ntfs-3g doesn't exist ( and it sounds like it doesn't ) then you will be left with a read only file system.

Install ntfs-3g or at least find out if it's already installed:
```
sudo apt-get install ntfs-3g
```

[COLOR=Blue]**EDIT**[/COLOR]: Sorry, must have posted right past each other - never mind :oops:

---

