---
title: "My backup plan"
date: 2011-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by fritzman on 2011-06-07
I'm sure we all know, or should know, the importance of keeping a backup of our important stuff.  And I'm sure we all know the importance of regular and frequent backups.  Yet, all too often, I'm asked to assist friends and relatives in trying to recover files, pictures, music, documents, et al, from damaged hard drives.  When I ask about their most recent backup, I'm greeted with, sometimes, a blank stare, or the look of a deer caught in the headlights, or the sheepish, eyes-downcast admission that they don't have a recent one, or that their backup was on the same drive as the one that just crashed.
My backup plan, I'm certain, is NOT new, nor original.  It might be just a bit unique in that it is a fully functional, boot-able clone of my primary hard drive.  You may NOT be able to make yours boot-able depending on your bios, especially if you have a lap-top computer.  But, the basic plan will work, even if it isn't a boot-able clone.
I have a desktop computer with a 750G sata hard drive, and a spare bay and a spare sata port.  I purchased an identical 750G hard drive, and installed it.  I then partitioned it, using GPARTED, with the same layout as my main hard drive; a 2G SWAP partition, a 40G / partition as ext4, and the rest as an ext3 partition for /home.  (I know!  That's a huge /home partition!  I like to play around with other OS's using VirtualBox, including Windows XP, Windows 7, openSUSE, Fedora, etc.)
Then, I made two bkup directories in the / partition, /bkup and /bkhome.  Then I edited /etc/fstab to mount the new partitions on the new hard drive.  Here is my /etc/fstab;

al@uglybox:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.

#

# Use 'vol_id --uuid' to print the universally unique identifier for a

# device; this may be used with UUID= as a more robust way to name devices

# that works even if disks are added and removed. See fstab(5).

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# / was on /dev/sda2 during installation

UUID=1552dd84-cb7b-4b45-a2d2-530917588824 / ext4    relatime,errors=remount-ro 0 1

#/dev/sda2	/               ext4    relatime,errors=remount-ro 0 1



# /home was on /dev/sda4 during installation

UUID=3e1bd513-7446-49f2-b44d-3453b008f5a0 /home ext3    relatime        0       2

#/dev/sda4	/home           ext3    relatime        1 2



# /bkup was on /dev/sdb2 during installation with bootable copy of /sda2

UUID=d4c1e96e-cd70-4a08-9de7-7d664757629f /bkup           ext4    rw,noauto,user,exec        1 2

#/dev/sdb2	/bkup           ext4    rw,noauto,user,exec        1 2



# /bkhome was on /dev/sdb3 during installation with copy of /sda4

UUID=2128d97e-b742-464f-b4bd-6267ed18c67b /bkhome           ext3	rw,noauto,user,exec        1 2

#/dev/sdb3	/bkhome         ext3	rw,noauto,user,exec        1 2



# /wd1 was on /dev/sdf1 (western digital usb drive) during installation

UUID=08BD-7D3F  /wd1           vfat	rw,noauto,user,exec        1 2

#/dev/sdf1	/wd1           vfat	rw,noauto,user,exec        1 2



# /wd2 was on /dev/sdf2 (western digital usb drive) during installation

UUID=fe88f9c5-34cf-448e-836d-1d1f89bcb245  /wd2           ext4	rw,noauto,user,exec        1 2

#/dev/sdf2	/wd2           ext4	rw,noauto,user,exec        1 2



# /wd3 was on /dev/sdf3 (western digital usb drive) during installation

UUID=99e06175-6393-40f0-b6cf-f59469d585ee  /wd3           ext3	rw,noauto,user,exec        1 2

#/dev/sdf1	/wd3           ext3	rw,noauto,user,exec        1 2



# /wd-sr2 was on /dev/sr2 during installation

/dev/sr2	/wd-sr2	      udf	noauto,user,exec	1 2



# /kingston2g was on /dev/sdd1 (kingston 2g travel drive) during installation

UUID=0D78-CFBE  /kingston2g          vfat	rw,noauto,user,exec       1 2

#/dev/sdd1	/kingston2g          vfat	rw,noauto,user,exec        1 2



# /kingston8g was on /dev/sde1 (kingston 8g travel drive) during installation

UUID=0FC5-AB33  /kingston8g          vfat	rw,noauto,user,exec        1 2

#/dev/sde1	/kingston8g          vfat	rw,noauto,user,exec        1 2



# swap was on /dev/sda1 during installation

UUID=4785f967-4566-4397-84a1-09bccd697127 none            swap    sw              0       0

#/dev/sda1	none            swap    sw              0       0



# swap was on /dev/sdb1 during installation

#UUID=838b5b10-7396-4651-ae20-98538f8b9783 none            swap    sw              0       0

#/dev/sdb1	none            swap    sw              0       0



/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/srd2        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Next, I mounted the / partition of the new drive;
al@uglybox:~$ mount /bkup
al@uglybox:~$ cd /
al@uglybox:/$ ls /

bin	 dev	     lib	 net   selinux	vmlinuz      xorg.conf

bkhome	 etc	     lib32	 opt   srv	vmlinuz.old  xorg.conf.backup

bkup	 home	     lib64	 proc  sys	wd1

boot	 initrd.img  lost+found  root  tmp	wd2

cdrom	 kingston2g  media	 save  usr	wd3

cleanup  kingston8g  mnt	 sbin  var	wd-sr2
al@uglybox:/$ ls bkup

DO NOT try to copy /sys, nor /proc, nor any mounted device, such as usb drives or CD's to the new partition, as they are in use, and are dynamic.  Doing so COULD cause serious problems, as with /sys or /proc, or fill up the / partition with data on the mounted drives.  Instead, make directories for those dynamic or mounted directories;

al@uglybox:/$ sudo mkdir /bkup/home
al@uglybox:/$ sudo mkdir /bkup/kingston2g
al@uglybox:/$ sudo mkdir /bkup/kingston8g

al@uglybox:/$ sudo mkdir /bkup/media
al@uglybox:/$ sudo mkdir /bkup/proc

al@uglybox:/$ sudo mkdir /bkup/sys

Then, copy the rest of your / directories;

al@uglybox:/$ sudo cp -rauvd /boot /bkup
al@uglybox:/$ sudo cp -rauvd /dev /bkup

&#8230;...........................and so on, till you have an exact match of the two / directories;

al@uglybox:/$ ls /

bin	 dev	     lib	 net   selinux	vmlinuz      xorg.conf

bkhome	 etc	     lib32	 opt   srv	vmlinuz.old  xorg.conf.backup

bkup	 home	     lib64	 proc  sys	wd1

boot	 initrd.img  lost+found  root  tmp	wd2

cdrom	 kingston2g  media	 save  usr	wd3

cleanup  kingston8g  mnt	 sbin  var	wd-sr2

al@uglybox:/$ ls bkup

bin	 dev	     lib	 net   selinux	vmlinuz      xorg.conf

bkhome	 etc	     lib32	 opt   srv	vmlinuz.old  xorg.conf.backup

bkup	 home	     lib64	 proc  sys	wd1

boot	 initrd.img  lost+found  root  tmp	wd2

cdrom	 kingston2g  media	 save  usr	wd3

cleanup  kingston8g  mnt	 sbin  var	wd-sr2

Next, mount /bkhome;

al@uglybox:/$ mount /bkhome
al@uglybox:/$ sudo chown al /bkhome
al@uglybox:/$ mount /bkhome/*
al@uglybox:/$ cp -rauvd /home/al /bkhome

Now, we need to edit /bkup/etc/fstab to account for the drive/mount-point changes;

al@uglybox:/$ sudo gedit /bkup/etc/fstab

[sudo] password for al:
# /etc/fstab: static file system information.

#

# Use 'vol_id --uuid' to print the universally unique identifier for a

# device; this may be used with UUID= as a more robust way to name devices

# that works even if disks are added and removed. See fstab(5).

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# / was on /dev/sdb2 during installation

UUID=d4c1e96e-cd70-4a08-9de7-7d664757629f / ext4    relatime,errors=remount-ro 0 1

#/dev/sdb2	/               ext4    relatime,errors=remount-ro 0 1



# /home was on /dev/sdb3 during installation

UUID=2128d97e-b742-464f-b4bd-6267ed18c67b /home ext3    relatime        0       2

#/dev/sdb3	/home           ext3    relatime        1 2



# /sda2 was on /dev/sda2 during installation as a bootable copy of /sdb2

UUID=1552dd84-cb7b-4b45-a2d2-530917588824 /bkup           ext4	noauto,user,exec        1 2

#/dev/sda2	/bkup           ext4	noauto,user,exec        1 2



# /sda4 was on /dev/sda4 during installation as a complete copy of sda4

UUID=3e1bd513-7446-49f2-b44d-3453b008f5a0 /bkhome           ext3    noauto,user,exec        1 2

#/dev/sda4	/bkhome           ext3    noauto,user,exec        1 2



# /wd1 was on /dev/sdf1 (western digital usb drive) during installation

UUID=08BD-7D3F  /wd1           vfat	noauto,user,exec        1 2

#/dev/sde1	/wd1           ext3	noauto,user,exec        1 2



# /wd2 was on /dev/sdf1 (western digital usb drive) during installation

UUID=fe88f9c5-34cf-448e-836d-1d1f89bcb245 /wd2           ext4	noauto,user,exec        1 2

#/dev/sde1	/wd2           ext4	noauto,user,exec        1 2



# /wd3 was on /dev/sdf1 (western digital usb drive) during installation

UUID=99e06175-6393-40f0-b6cf-f59469d585ee /wd3           ext3	noauto,user,exec        1 2

#/dev/sde1	/wd3           ext4	noauto,user,exec        1 2



# /wd-sr2 was on /dev/sr2 during installation

/dev/sr2	/wd-sr2	      udf	noauto,user,exec	1 2



# /kingston2g was on /dev/sdd1 (kingston 2g travel drive) during installation

UUID=0D78-CFBE  /kingston2g          vfat	noauto,user,exec        1 2

#/dev/sdd1	/kingston2g          ext3	rw,noauto,user,exec        1 2



# /kingston8g was on /dev/sde1 (kingston 8g travel drive) during installation

UUID=0FC5-AB33  /kingston8g          vfat	noauto,user,exec        1 2

#/dev/sdf1	/kingston8g          ext3	rw,noauto,user,exec        1 2



# swap was on /dev/sda1 during installation

#UUID=4785f967-4566-4397-84a1-09bccd697127 none            swap    sw              0       0

#/dev/sda1	none            swap    sw              0       0



# swap was on /dev/sdb1 during installation

UUID=838b5b10-7396-4651-ae20-98538f8b9783 none            swap    sw              0       0

#/dev/sdb1	none            swap    sw              0       0



/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/scd0       /home/al/media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

And, now, using Gnome-Schedule, we make a simple cron job for our backup.  The frequency of the cron job is up to you, of-course, but, in general, the more frequent the backup, the less likely you'll lose precious data.  It isn't absolutely necessary to keep a current backup of your operating system files, but the older your backup files are, the more likely you are to experience problems, or at least endure a lengthy update of your system when/if you do have to boot to your backup drive.  For me, a daily backup of my /home directory, and a weekly backup of your /boot, /etc, /lib, /opt, /usr, and /var directories is sufficient.  Your needs/desires may be different.  To set up your backup of these directories, you'll need to do this as 'root, while the backup of your /home/al directory can be done as user.

al@uglybox:/$ sudo gnome-schedule

The use of gnome-schedule is really straight-forward.  The cron job you build will be kept in the home directory of whomever made it; e.g. as root, it would be found in /root/.gnome/gnome-schedule/crontab  

(See the attached thumbnail, "gnome-schedule-root.jpg")


al@uglybox:/$ sudo ls /root/.gnome/gnome-schedule/crontab

1  10  11  12  13  14  15  2  9  last_id
Please note in the screen-shot above the second entry!  You will need to copy the &#8220;good&#8221; /bkup/etc/fstab file to a safe place (In my case, I've made a &#8220;save&#8221; directory in /) so that you can restore it after your backup has completed.  This is important, because if you forget to do that, you'll boot right back to your primary drive, or the boot might hang.  Note the eighth entry copies your saved &#8220;fstab&#8221; file back into /bkup/etc/fstab.  Also note that the final entry actually occurs during the scheduled backup at 02:03.  When I built this cron job, I had overlooked the possibility that an update of the kernel would have changed the contents of /boot.  The order in which they appear in your job doesn't matter, as long as the time it is scheduled to happen is correct.

or for user-al;

(See the attached thumbnail, "gnome-schedule-al.jpg")


al@uglybox:~$ ls .gnome/gnome-schedule/crontab

1  10  11  12  13  14  2  27  28  3  4	5  6  7  8  9  last_id

Note that, if you use the command, cp -ruavd, it will be a recursive copy, including directories, and it will only copy what ever has changed since the last incident of 'cp' of that directory.
After each step of building your boot-able backup, it is wise to test the functionality of your progress.
For example, after I get the new hard drive set up, and edit the /etc/fstab file on the new drive, I edit the /boot/grub/menu.lst and make an entry for the new drive.  Then I reboot and test it;

al@uglybox:~$ sudo gedit /boot/grub/menu.lst

color white/blue black/black



default		0



timeout		10



#hiddenmenu



splashimage=(hd0,1)/boot/grub/penguin-inside.xpm.gz



title Ubuntu 11.04 64bit sda2 (kernel 2.6.38-8-generic)

	root	(hd0,1)

	kernel	/boot/vmlinuz-2.6.38-8-generic root=UUID=1552dd84-cb7b-4b45-a2d2-530917588824 ro quiet splash 

	initrd	/boot/initrd.img-2.6.38-8-generic

	quiet



title Ubuntu 11.04 64bit sdb2 (kernel 2.6.38-8-generic)

	root	(hd1,1)

	kernel	/boot/vmlinuz-2.6.38-8-generic root=UUID=d4c1e96e-cd70-4a08-9de7-7d664757629f ro quiet splash 

	initrd	/boot/initrd.img-2.6.38-8-generic

	quiet
Also, note that the use of &#8220;root=UUID=xxxxx&#8221; assures us that we'll actually hit the intended target, whereas using the &#8220;root=/dev/sdxx&#8221; can, sometimes, fail, since the device naming can sometimes change, depending on whether we have removed or added usb devices since the last reboot.

I hope this is helpful.  Feedback is welcome, as are tips for improvements.  None of us has all the answers all of the time.  

owa

---

