---
title: "HELP! /home is not present or is not ready"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by Nodin092004 on 2012-10-11
I'm still very new with Ubuntu and I'm afraid I may have permanently damaged my /home partition. I appreciate any and all advice, but please provide clear, detailed instructions for me to follow.

I have 12.04, the only OS on my Sony VAIO. It started with messages that my /boot partition was getting low (~250MB left), my computer shutting down randomly, acting very laggy, and that there were some serious damage to my hard drive: >100 bad sectors according to Disk Utility which I then fixed and brought down to (currently but keeps on climbing higher) 8. So I decided to expand /boot from ~7.5GB to 10GB by reallocating 2.5GB from /home to the /boot partition using GParted.

This is where my first problem came in: although I successfully created 2.5GB of unallocated space from the /home (sda7) partition, it always ended up on the RIGHT side of /home instead of the LEFT side next to the /boot (sda6) partition. I kept trying to move /home to the RIGHT of the 2.5GB of unallocated space but each time GParted gave me an error message half-way through and could not complete the task. So, I tried to move /boot up against /home by moving it RIGHT to hopefully get it closer, but I couldn't get it "close enough" to /home to switch with it to get next to the unallocated space (I apologize if this sounds very rudimentary but again I'm very new to this and have only been following the advice of other forum posts) because a few megabytes of space always separated it from the /home partition. So, as a final shot, I tried to move /home LEFT so it's closer to /boot and could perhaps swap it that way - GParted was about half-way through the task when an error message appeared like before, except now this time a serious warning appeared where there was none before: Unable to detect file system! (See the screenshot attached for the GParted breakdown.)

I tried restarting my system and all that came up was: The disk drive for /home is not present or not ready. When I tried the option to (S)kip it, it would go to the log-in screen which would then flash after entering the password and go back to the log-in. When I tried the (M)anual option, it would bring me to a terminal-like command which left me stumped. I even tried using Boot-Repair from a live USB but that didn't solve anything.

No, I did not back up ANY of my data before executing any of these procedures (I don't have an external hard drive and can't afford one), which I realize is very stupid but I had no other option and *thought* it would be a simple procedure. So, my hard drive issues, my lack of space on /boot, and my inability to even access /home anymore are my biggest issues right now - any help is greatly appreciated!! 

I just want my computer back! :(

---

### Post by Nodin092004 on 2012-10-11
By the way, some useful data:

> ubuntu@ubuntu:~$ sudo du -hs /*
6.4M    /bin
2.6M    /boot
695M    /cdrom
428K    /dev
7.8M    /etc
du: cannot access `/home/ubuntu/.gvfs': Permission denied
50M    /home
0    /initrd.img
125M    /lib
0    /media
0    /mnt
0    /opt
du: cannot access `/proc/4783/task/4783/fd/4': No such file or directory
du: cannot access `/proc/4783/task/4783/fdinfo/4': No such file or directory
du: cannot access `/proc/4783/fd/4': No such file or directory
du: cannot access `/proc/4783/fdinfo/4': No such file or directory
0    /proc
1.8G    /rofs
8.0K    /root
9.1M    /sbin
0    /selinux
0    /srv
0    /sys
12K    /tmp
1.5G    /usr
105M    /var
0    /vmlinuz


> ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.5G   65M  1.5G   5% /
none                  1.5G  304K  1.5G   1% /dev
/dev/sdb1             1.9G  695M  1.2G  37% /cdrom
/dev/loop0            667M  667M     0 100% /rofs
none                  1.5G  124K  1.5G   1% /dev/shm
tmpfs                 1.5G   12K  1.5G   1% /tmp
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw


> ubuntu@ubuntu:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.5G   65M  1.5G   5% /
none      devtmpfs    1.5G  304K  1.5G   1% /dev
/dev/sdb1     vfat    1.9G  695M  1.2G  37% /cdrom
/dev/loop0
          squashfs    667M  667M     0 100% /rofs
none         tmpfs    1.5G  124K  1.5G   1% /dev/shm
tmpfs        tmpfs    1.5G   24K  1.5G   1% /tmp
none         tmpfs    1.5G   88K  1.5G   1% /var/run
none         tmpfs    1.5G     0  1.5G   0% /var/lock
none         tmpfs    1.5G     0  1.5G   0% /lib/init/rw


> ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


> ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HM321HI (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  300MB   299MB   primary   ext2            boot
 2      301MB   320GB   320GB   extended
 5      301MB   2300MB  1999MB  logical   linux-swap(v1)
 6      2303MB  10.3GB  7995MB  logical   ext4
 7      10.3GB  317GB   307GB   logical


Model: FLASH Drive SM_USB20 (scsi)
Disk /dev/sdb: 2006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      262kB  2006MB  2006MB  primary  fat32        boot, lba



---

### Post by sandyd on 2012-10-11
> **Nodin092004 said:**
> I'm still very new with Ubuntu and I'm afraid I may have permanently damaged my /home partition. I appreciate any and all advice, but please provide clear, detailed instructions for me to follow.

I have 12.04, the only OS on my Sony VAIO. It started with messages that my /boot partition was getting low (~250MB left), my computer shutting down randomly, acting very laggy, and that there were some serious damage to my hard drive: >100 bad sectors according to Disk Utility which I then fixed and brought down to (currently but keeps on climbing higher) 8. So I decided to expand /boot from ~7.5GB to 10GB by reallocating 2.5GB from /home to the /boot partition using GParted.

This is where my first problem came in: although I successfully created 2.5GB of unallocated space from the /home (sda7) partition, it always ended up on the RIGHT side of /home instead of the LEFT side next to the /boot (sda6) partition. I kept trying to move /home to the RIGHT of the 2.5GB of unallocated space but each time GParted gave me an error message half-way through and could not complete the task. So, I tried to move /boot up against /home by moving it RIGHT to hopefully get it closer, but I couldn't get it "close enough" to /home to switch with it to get next to the unallocated space (I apologize if this sounds very rudimentary but again I'm very new to this and have only been following the advice of other forum posts) because a few megabytes of space always separated it from the /home partition. So, as a final shot, I tried to move /home LEFT so it's closer to /boot and could perhaps swap it that way - GParted was about half-way through the task when an error message appeared like before, except now this time a serious warning appeared where there was none before: Unable to detect file system! (See the screenshot attached for the GParted breakdown.)

I tried restarting my system and all that came up was: The disk drive for /home is not present or not ready. When I tried the option to (S)kip it, it would go to the log-in screen which would then flash after entering the password and go back to the log-in. When I tried the (M)anual option, it would bring me to a terminal-like command which left me stumped. I even tried using Boot-Repair from a live USB but that didn't solve anything.

No, I did not back up ANY of my data before executing any of these procedures (I don't have an external hard drive and can't afford one), which I realize is very stupid but I had no other option and *thought* it would be a simple procedure. So, my hard drive issues, my lack of space on /boot, and my inability to even access /home anymore are my biggest issues right now - any help is greatly appreciated!! 

I just want my computer back! :(It looks like your /home partition is dead.

Have you tried using testdisk to recover your data?

FYI - if there were hdd problems as bad as this, I would reccomend getting a new hard drive - the hard drive could die and lose all your data someday

---

### Post by Wim Sturkenboom on 2012-10-11
I don't know how important your data is to you, but unless you can restore the partitions to the original state, a re-install is the best option (in my opinion).

If your data is important, you need to get your hands on an external HD (borrow one if there are no other options). Use a liveCD, temporarily install testdisk (it's in the repos) and let it try to recover your data.

After the facts:
1)
There was no reason for panic. You could have cleaned out /boot (remove a few old kernels).
2)
sda6 is NOT /boot, sda1 more than likely is; sda6 is the root partition (by the looks of it)
3)
Two remarks regarding your partitioning. Why a separate boot partition; I've given that one up long ago for desktops. And your root partition might be a bit small; I would allocate a bit more (if it comes to a re-install); between 10GB and 25GB depending on how much extra SW you install.

And I guess "lesson learned"; never mess with partitions if you don't have backups.

Good luck

---

### Post by DuckHook on 2012-10-11
As others have already noted, this situation looks grim. If you are still intent on trying a rescue, download *System Rescue CD* from here:

[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

burn the ISO onto a CD and boot up with it. There are too many utilities to get into here, but this is your only chance. To be honest, the chance is slim, but then, you may take the view that there is nothing more to lose.

If you have critical data that you simply must recover, then *don't do anything more to your HD*, including System Rescue CD. Instead take it to a data recovery shop and they may be able to recover your most critical data. It won't be cheap, but it is the best way at this point to salvage what you need.

If SRCD can't recover and you decide on a new install, then sandyd is correct: this HD is bad news. Throw it away and install on a new HD. Back up properly from now on and invest in an external drive. It goes without saying that, in future, do not touch partitions unless you are prepared to hose your installation. If you go in with this mindset, you will be prepared (and backed up) for anything that may happen.

---

### Post by oldfred on 2012-10-11
The yellow triangle in gparted is a warning. If you click (right click?) on it what does it say.

Have you run e2fsck on sda6?

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb6
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb6


But if you are getting bad sectors and they are growing that is a bad sign on life of hard drive.

Did you make so many partition changes that the UUID changed? Usually it does not, but if it did then your fstab entry may be wrong. Verify that UUID of /home is correct:
# To clear cache and get new view:
sudo blkid -c /dev/null -o list
sudo cat /etc/fstab

---

### Post by Nodin092004 on 2012-10-16
> **Wim Sturkenboom said:**
> I don't know how important your data is  to you, but unless you can restore the partitions to the original state,  a re-install is the best option (in my opinion).

If your data is important, you need to get your hands on an external HD  (borrow one if there are no other options). Use a liveCD, temporarily  install testdisk (it's in the repos) and let it try to recover your  data.

After the facts:
1)
There was no reason for panic. You could have cleaned out /boot (remove a few old kernels).
2)
sda6 is NOT /boot, sda1 more than likely is; sda6 is the root partition (by the looks of it)
3)
Two remarks regarding your partitioning. Why a separate boot partition;  I've given that one up long ago for desktops. And your root partition  might be a bit small; I would allocate a bit more (if it comes to a  re-install); between 10GB and 25GB depending on how much extra SW you  install.

And I guess "lesson learned"; never mess with partitions if you don't have backups.

Good luck

1) How do I go about removing old kernels from /boot?

2) Sorry, you're completely right, I meant to say /root (sda6) whenever I said /boot - I have no idea what the difference between the two is. 

3) I have no idea why there is a separate /boot partition, that is just the advice I took from some online tutorial. I realize *now* that my /root partition is too small, that's exactly what caused all this havoc in the first place and why I was trying to expand it to 10GB. 

> **DuckHook said:**
> As others have already noted, this situation  looks grim. If you are still intent on trying a rescue, download *System Rescue CD* from here:

[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

burn the ISO onto a CD and boot up with it. There are too many utilities  to get into here, but this is your only chance. To be honest, the  chance is slim, but then, you may take the view that there is nothing  more to lose.

If you have critical data that you simply must recover, then *don't do anything more to your HD*,  including System Rescue CD. Instead take it to a data recovery shop and  they may be able to recover your most critical data. It won't be cheap,  but it is the best way at this point to salvage what you need.

If SRCD can't recover and you decide on a new install, then sandyd is  correct: this HD is bad news. Throw it away and install on a new HD.  Back up properly from now on and invest in an external drive. It goes  without saying that, in future, do not touch partitions unless you are  prepared to hose your installation. If you go in with this mindset, you  will be prepared (and backed up) for anything that may happen.

Thanks for the tips, I guess I'll try testdisk and if that can't solve it I'll try to get the data recovered elsewhere...

> **oldfred said:**
> The yellow triangle in gparted is a warning. If you click (right click?) on it what does it say.

Have you run e2fsck on sda6?

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb6
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb6


But if you are getting bad sectors and they are growing that is a bad sign on life of hard drive.

Did you make so many partition changes that the UUID changed? Usually it  does not, but if it did then your fstab entry may be wrong. Verify that  UUID of /home is correct:
# To clear cache and get new view:
sudo blkid -c /dev/null -o list
sudo cat /etc/fstab

The yellow triangle says: 
> 
[I]Unable to detect file system! Possible reasons are:
-The file system is damaged
-The file system is unknown to GParted
-There is no files system available (unformatted)[/I]I ran e2fsck, here's the output (I changed *sdb6* to *sda6*):

> 
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb6
e2fsck: No such file or directory while trying to open /dev/sdb6
/dev/sdb6: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda6
                                                                               
  296371 inodes used (60.65%)
     223 non-contiguous files (0.1%)
     453 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 240612/99
 1293506 blocks used (66.27%)
       0 bad blocks
       1 large file

  190004 regular files
   33258 directories
      57 character device files
      25 block device files
       0 fifos
      35 links
   73018 symbolic links (55568 fast symbolic links)
       0 sockets
--------
  296397 files
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdb6
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open /dev/sdb6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda6
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  296371 inodes used (60.65%)
     223 non-contiguous files (0.1%)
     453 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 240612/99
 1293506 blocks used (66.27%)
       0 bad blocks
       1 large file

  190004 regular files
   33258 directories
      57 character device files
      25 block device files
       0 fifos
      35 links
   73018 symbolic links (55568 fast symbolic links)
       0 sockets
--------
  296397 files
ubuntu@ubuntu:~$ 
And the output from UUID testing:

> 
ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /rofs          
/dev/sda1  ext2             (not mounted)  fdcc2f22-c7db-4640-9c13-e203327cbbba
/dev/sda5  swap             <swap>         65f4ac27-8c84-4676-a64a-bdd49931d7d5
/dev/sda6  ext4             (not mounted)  093029c1-2d49-4d97-b50f-9503bbbb38f4
/dev/sdb1  vfat    PENDRIVE /cdrom         16FC-190A
ubuntu@ubuntu:~$ sudo cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ 
Again, oldfred, I can't really confirm whether these data are correct or not as I'm a total newbie...

---

### Post by oldfred on 2012-10-16
The e2fsck example was sdb6 where you need to change to your partition(s). It looks like it ran ok with your sda6 partition.

Can you mount sda6 now?

Or if it is your /home do this mount it as this reruns fstab?

sudo mount -a

---

