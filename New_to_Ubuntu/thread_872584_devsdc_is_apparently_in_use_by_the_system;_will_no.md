---
title: "/dev/sdc is apparently in use by the system; will not make a filesystem here!"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by abriejo on 2008-07-28
Hi All


After having created a RAID0 set of three disks , using software RAID0 with the mdadm utility, I found out that the three 1TB disks will not provide adequate space.I decided to add another 1TB disk and recreate the RAID0 array.I have now added another disk, deleted the RAID array using sudo mdadm --stop /dev/md0, made sure none of the disks or the array is still mounted and recreated the partitions on each of the four disks.On the third disk, however(/dev/sdc1) , I am unable to create the ext3 file system.

I get the following message :

/dev/sdc1 is apparently in use by the system; will not make a filesystem here!

Since I recreated the partitions on each disk,including /dev/sdc there must be some program or service reserving the disk.
Please help me to get rid of this message so I may go ahead and create the ext3 file system?

thanks

---

### Post by eightmillion on 2008-07-28
Is the drive mounted? Can you run the command "sudo fuser -v /dev/sdc" to see if any programs are accessing it?

---

### Post by abriejo on 2008-07-28
Hi


I ran "sudo fuser -v /dev/sdc" but nothing happens.No error, no confirmation.

---

### Post by eightmillion on 2008-07-28
And is the drive mounted? Can you paste the output of 'mount'?

---

### Post by abriejo on 2008-07-28
Hi


The drive is not mounted.
Here is the result :

/dev/sde1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/abriejo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=abriejo)

---

### Post by eightmillion on 2008-07-28
Have you rebooted since recieving this error?

---

### Post by abriejo on 2008-07-28
Yes, I have rebooted several times.

---

### Post by eightmillion on 2008-07-28
Could you try creating the filesystem manually?
> 
sudo mkfs.ext3 /dev/hdc1


---

### Post by abriejo on 2008-07-28
Yes, I have.That is when I receive the error in the subject of this mail.I also get the same error on gparted.

---

### Post by abriejo on 2008-07-29
Hi

Any other ideas on how to get Ubuntu to let go of my disk?

thanks

---

### Post by eightmillion on 2008-07-29
Sorry, I kept getting 503s earlier when trying to connect to ubuntuforums. Have you thought about booting a live cd and trying to create the filesystem on the drive?

---

### Post by abriejo on 2008-07-30
Hi

I was about to try the CD startup when I tried one last thing again.

sudo mdadm --stop /dev/md0

It worked, but I find it strange because I did it before and md0 did not appear in the fdisk -l screen.

Immdiately after that I was able to run the sudo mkfs.ext3 /dev/sdc 


Maybe it is because I ran the zero-superblock tasks overnight - something that made me nervous, since I have no idea what it does.

Than You for your help!

---

### Post by Lexicon101 on 2008-07-30
have you tried deleting and recreating the partition?
(Sorry if it's an obvious question. Or if there's no way for you to do that..)
Actually, I have no experience with RAID arrays, but that's the only thing I can think of.. wipe it and try again.. You probably don't have any data on it, or you wouldn't be making a filesystem..

EDIT: Ahaha. I didn't check the second page.
Never mind me.

---

### Post by abriejo on 2008-07-30
Hi


I have done that and the space is still being taken up.
Any specialists in mdadm software RAID out there?
I am using RAID0, so the RAID overhead should be minimal , not 186GB.I am also not so sure that it is RAID overhead occupying the space.

thanks

---

### Post by abriejo on 2008-07-30
Does anybody have any idea why 186GB of space is taken up on my 4 * 1TB mdadm RAID0 array, even when there are no files present on it?

---

### Post by abriejo on 2008-07-31
In case anyone is interested :

It was no that complicated.
I ran 'tune2fs -i 0 -c 0 -r 0 -m 0 /dev/md0'

---

### Post by alkemnation on 2008-08-04
I had the same problem in SUSE 10. I had to disable the multipathing services

chkconfig boot.multipath off

chkconfig multipathd off

I could tell multipathing was enabled because I saw a dm-0 device when I did an fdisk -l

Disk /dev/dm-0: 16.1 GB, 16106127360 bytes
64 heads, 32 sectors/track, 15360 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Once these where off, I was able to format it.

I am now looking into what commands I will need in the future to accomplish this without turning multipathing services off

Hope this helps

---

### Post by stuen93 on 2009-09-11
I had a similar problem as well but it was because the drive was part of a volume group, after I removed the drive from the group everything worked fine.

---

### Post by rich_in_sheboygan on 2011-06-29
Sorry to reply to an old post, but I ran into this same problem and none of the suggestions fixed the issue.  However, it gave me a good head start.   My hard drives were new out of the box, and Ubuntu Linux Server (9.0) could see them and Fdisk yeilded a partition, but I could not write the file system.  
 
The Gigabyte motherboard I was using had some sort of "quick install" process for optimizing the BIOS, and I think when I ran that (should have read closer before hitting yes ... oops!) I think it maybe set up some sort of RAID interface with the hardware. 
 
I tried to reset the BIOS to factory defaults, and redo the partitions... no luck. 
 
I finished by turning the RAID back on, saving it, going into the RAID BIOS, deleting a partition there, then exiting, putting the BIOS back to standard (not RAID), and then...
 
... it worked fine :)  
 
Thanks for the help!   I'd still be beating my head against the wall otherwise.   While the solutions posted didn't fix it, knowing that software RAIDS caused this in the past led me to track down the hardware RAID changes in the BIOS.  
 
Rich

---

### Post by mikiemorales on 2011-09-06
> **abriejo said:**
> Hi

I was about to try the CD startup when I tried one last thing again.

sudo mdadm --stop /dev/md0

It worked, but I find it strange because I did it before and md0 did not appear in the fdisk -l screen.

Immdiately after that I was able to run the sudo mkfs.ext3 /dev/sdc 


Maybe it is because I ran the zero-superblock tasks overnight - something that made me nervous, since I have no idea what it does.

Than You for your help!


It worked for me. Thanks!

---

