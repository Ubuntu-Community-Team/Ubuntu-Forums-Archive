---
title: "Reorganize hard disk partitions"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by Dimoutlook on 2012-03-12
Ok what I would like to do is wipe win 7 off my hard drive and run Ubuntu exclusively,
I was looking at a 1 Tb hard drive and making 1 primary partition and six extended partitions.That would display on the desktop.

How could I do this, Please remember that I'm the poster child for the how to dummies books, if you could explain it in a simple way I would be forever grateful 

Thank you

Dimoutlook

---

### Post by papibe on 2012-03-12
Hi Dimoutlook.

You can do that with 'gparted'. However, you need to do it using a Live CD. Use the Ubuntu installation CD, but choose try Ubuntu instead of install it. Once on the desktop, launch gparted.

I would fairly easy if you want to either install Ubuntu for the first time, or erase everything on the disk. 

If you have Ubuntu installed already and wants to keep it, it would be more tricky.

Just some thoughts.
Regards.

---

### Post by Dimoutlook on 2012-03-12
Thank you i will be formating the drive then make the partitions,tricky
part is having the indavidual drive names show on the desktop is there a way to do that?

Thank you
Dimoutlook

---

### Post by NikTh on 2012-03-12
> **Dimoutlook said:**
> Thank you i will be formating the drive then make the partitions,tricky
part is having the indavidual drive names show on the desktop is there a way to do that?

Thank you
Dimoutlook

Hi , 
no its not tricky. After you finish the partitioning - installation of Ubuntu  and all working properly then open a terminal and install "gnome-tweak-tool" ```
sudo apt-get install gnome-tweak-tool
``` . After installation finish open Dash and search for " advanced settings" open it and at the Desktop section you will see " show mounted volumes on the desktop" turn it ON and Done !

---

### Post by Dimoutlook on 2012-03-13
Thank you NikTh, that will defiantly make my day. I had no idea that it would be that simple

Dimoutlook

---

### Post by Dimoutlook on 2012-03-13
Well this is embarrassing g-parted worked its magic and have all the
partitions named and mounted, But I cant read or write to them as
I don't have root permission to do so, any attempt just gives
"root setuid" error nothing I've done so far has worked. How do I
get root permission so I can fix this, partitions are named Files,
Movies,music,Temp,Ebooks. any thoughts welcome.

Dimoutlook

---

### Post by papibe on 2012-03-13
Could you post the result if these commands? (it may give us some clues about what is happening).

```
sudo fdisk -l

mount -l

cat /etc/fstab
```
Regards.

---

### Post by Dimoutlook on 2012-03-13
dim@LP-1:~$ sudo fdisk -l
sudo: must be setuid root

dim@LP-1:~$ mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dim)
/dev/sda5 on /media/Files type ext4 (rw,nosuid,nodev,uhelper=udisks) [Files]
/dev/sda6 on /media/Movies type ext4 (rw,nosuid,nodev,uhelper=udisks) [Movies]
/dev/sda7 on /media/music type ext4 (rw,nosuid,nodev,uhelper=udisks) [music]
/dev/sda8 on /media/Temp type ext4 (rw,nosuid,nodev,uhelper=udisks) [Temp]
/dev/sda9 on /media/Ebook type ext4 (rw,nosuid,nodev,uhelper=udisks) [Ebook]
/dev/sr0 on /media/Ubuntu 11.10 amd64 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks) [Ubuntu 11.10 amd64]
dim@LP-1:~$ 

dim@LP-1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=89c6e27b-7bc2-4d48-8db8-1d64abbc1563 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=c2b177b7-cc61-4abc-8d98-c8a25c6c2730 none            swap    sw              0       0
dim@LP-1:~$ 


I hope I did this right I just copied from the terminal

Dimoutlook

---

### Post by papibe on 2012-03-13
I see that you have your partitions set up, but they are not set to be permanent (if you reboot you'll have to remount them again). For a permanent solution you need to add mount points to your /etc/fstab.

However, I think we need to solve your sudo problem first. It looks like a permission problem.

Could you post the result of this command:
```
ls -l /usr/bin/sudo
```
Regards.

---

### Post by adstri on 2012-03-13
I am having very similar issues to this but have windows installed and would like to keep it. 

[http://ubuntuforums.org/showthread.php?t=1940167](http://ubuntuforums.org/showthread.php?t=1940167)

can I use a similar method to fix my issues? 

Thanks 
Adam

---

### Post by Dimoutlook on 2012-03-13
Thank you for taking the time to help with this problem


dim@LP-1:~$ ls -l /usr/bin/sudo
-rwxr-xr-x 1 dim root 168768 2011-09-11 15:09 /usr/bin/sudo
dim@LP-1:~$ 


Dimoutlook

---

### Post by papibe on 2012-03-13
There's it is.

That it should look like this:
```
ls -l /usr/bin/sudo
-rwsr-xr-x 2 root root 127668 2011-01-19 12:01 /usr/bin/sudo

```
Since you can't 'sudo' to fix it, you need to boot into recovery mode. Then choose a root prompt in the next menu. To change the owner and permission back run this:
```
chown root:root /usr/bin/sudo

chmod 4755 /usr/bin/sudo
```
Then reboot.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by Dimoutlook on 2012-03-13
I can't even get into recovery mode I guess I will have to reinstall and just start over thank you for all your time spent helping me

Thank you
Dimoutlook

---

### Post by Dimoutlook on 2012-03-13
Ok I just did a new install and sudo is back to normal
Could we please tackel the /ect/fstab on how to put
the remaning devices in it I'm at a total loss on what
man fstab is telling me

Thank you
Dimoutlook

---

### Post by papibe on 2012-03-13
Sure.

Just to be extra safe, could you post (again) the result if these commands? (in case some things change, note that there's a new one).

```
sudo fdisk -l

mount -l

sudo blkid 

cat /etc/fstab
```
Regards.

---

### Post by Dimoutlook on 2012-03-13
dim@LP-1:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d02db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52211249    26105593+  83  Linux
/dev/sda2        52211311  1250258624   599023657    5  Extended
/dev/sda5        52211313   314359919   131074303+  83  Linux
/dev/sda6       314359983   576508589   131074303+  83  Linux
/dev/sda7       576508653   838657259   131074303+  83  Linux
/dev/sda8       838657323  1100805929   131074303+  83  Linux
/dev/sda9      1100805993  1242740204    70967106   83  Linux
/dev/sda10     1242740268  1250258624     3759178+  82  Linux swap / Solaris
dim@LP-1:~$ 

dim@LP-1:~$ mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dim)
dim@LP-1:~$ 


dim@LP-1:~$ sudo blkid 
/dev/sda1: UUID="790b1d99-10ab-4128-8289-9248ba0f9884" TYPE="ext4" 
/dev/sda5: LABEL="Files" UUID="0b4bc0aa-448f-4686-9afb-1beddf769568" TYPE="ext4" 
/dev/sda6: LABEL="Movies" UUID="acfafd6a-83f3-4ac5-891b-38514da6f941" TYPE="ext4" 
/dev/sda7: LABEL="Music" UUID="34af1fb9-b2c1-438c-9b6a-70b1efb2e7b8" TYPE="ext4" 
/dev/sda8: LABEL="Temp" UUID="6158f1f2-88c0-4af2-8105-58a0e0f8d398" TYPE="ext4" 
/dev/sda9: LABEL="Ebook" UUID="ca84b63d-9e96-499c-b5c5-9c1768b0b675" TYPE="ext4" 
/dev/sda10: UUID="c2b177b7-cc61-4abc-8d98-c8a25c6c2730" TYPE="swap" 
dim@LP-1:~$ 


dim@LP-1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=790b1d99-10ab-4128-8289-9248ba0f9884 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=c2b177b7-cc61-4abc-8d98-c8a25c6c2730 none            swap    sw              0       0
dim@LP-1:~$


Wow I never knew there was so much behind the scenes work in a OS

Thank you for being soo patient with me

Dimoutlook

---

### Post by papibe on 2012-03-13
I'm going to add one mount point, so you can understand how's done.

In post#2 you have:
> **/dev/sda5** on /media/Files type ext4 (rw,nosuid,nodev,uhelper=udisks) [Files]
So, what you want is to mount /dev/sda5 on /media/Files. The safe way to do that is reference the partition using its 'hardware ID' (from your previous post):
```
**/dev/sda5**: LABEL="Files" UUID="**0b4bc0aa-448f-4686-9afb-1beddf769568**" TYPE="ext4" 
```
Then you add the following line to your fstab:
```
# mount point for /media/Files
**UUID=0b4bc0aa-448f-4686-9afb-1beddf769568 /media/Files**     ext4    defaults    0    2

```
The rest mount points are similar.

An advice: make a copy of your working, unmodified fstab before modify it:
```
sudo cp /etc/fstab  /etc/fstab.old
```
Then, you can edit the file using gedit:
```
gksudo gedit /etc/fstab
```
Hope that helps, and tell us how it goes.
Regards.

BTW: for more details on fstab's format, check this [help page]("https://help.ubuntu.com/community/Fstab").

---

### Post by Dimoutlook on 2012-03-13
I can't thank you enough for all this help mabe some day I can
help some other one who needs to redo his hard drive


Thank you
Dimoutlook

---

### Post by Dimoutlook on 2012-03-13
Well got the fstab done but root is still hanging on for dear life
I still can't read or write to the partitions should I try to chown
with sudo?

Thank you Dimoutlook

---

### Post by Dimoutlook on 2012-03-13
BTW heres my fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=790b1d99-10ab-4128-8289-9248ba0f9884  /              ext4  errors=remount-ro    0  1  
# swap was on /dev/sda10 during installation
UUID=c2b177b7-cc61-4abc-8d98-c8a25c6c2730  none           swap  sw                   0  0  
UUID=0b4bc0aa-448f-4686-9afb-1beddf769568  /media/Files   ext4  defaults             0  2
UUID="acfafd6a-83f3-4ac5-891b-38514da6f941 /media/Movies  ext4  defaults             0  2  
UUID="34af1fb9-b2c1-438c-9b6a-70b1efb2e7b8 /media/Music   ext4  defaults             0  2 
UUID="6158f1f2-88c0-4af2-8105-58a0e0f8d398 /media/Temp    ext4  defaults             0  2 
UUID="ca84b63d-9e96-499c-b5c5-9c1768b0b675 /media/Ebook   ext4  defaults             0  2

---

### Post by papibe on 2012-03-13
Yes, try this:
```
sudo chown -R youruser:youruser  /media/Files
sudo chown -R youruser:youruser  /media/Movies
sudo chown -R youruser:youruser  /media/music
sudo chown -R youruser:youruser  /media/Temp
sudo chown -R youruser:youruser  /media/Ebook
```
Replaced 'youruser' as your actual username.

Regards.

---

### Post by bodhi.zazen on 2012-03-13
> **papibe said:**
> Yes, try this:
```
sudo chown -R youruser:youruser  /media/Files
sudo chown -R youruser:youruser  /media/Movies
sudo chown -R youruser:youruser  /media/music
sudo chown -R youruser:youruser  /media/Temp
sudo chown -R youruser:youruser  /media/Ebook
```
Replaced 'youruser' as your actual username.

Regards.

could just as easily

```
sudo chown -R youruser.youruser /media/*
```

---

### Post by Dimoutlook on 2012-03-13
Did not work root still rules surpreim

---

### Post by papibe on 2012-03-14
Could you post the result of these commands?
```
mount -l

ls -l /media
```
Regards.

---

### Post by bodhi.zazen on 2012-03-14
> **Dimoutlook said:**
> Did not work root still rules surpreim

What command did you run ?

---

### Post by Dimoutlook on 2012-03-14
A good nights sleep worked I redid the fstab this morning and it worked
finally I realy don't know what I would have done with out both of you
helping thank you both.

Thank you
Dimoutlook

---

