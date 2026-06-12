---
title: "Sata Drive Performce"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by mgbolts on 2008-09-19
Hi,

I installed Ubuntu 8.04 for the first time earlier this week. A review of issues prior to the install highlighted issues with sata drives with y MOBO. Accordingly, I used an older IDE drive, a WD250. The install went very well.

I have now come to install a second drive, a sata drive (1TB Caviar Black).

I could not find the drive on the system, I looked in the /dev folder and dev/disk.  However, the drive is visible in the bios.

After some research I found a common thread is to change the bios over to AHCI -> the drive was then detected and functioning.

However the performance of the drive is very poor. The old ide drive runs about 50% quicker than the new Caviar Black drive.  

The mobo is a Gigabyte EP45-DS3R.

Given that I plan to use this box as a file server, I need to get this drive working at decent speeds. Any suggestions?

---

### Post by Titan8990 on 2008-09-19
Post the output of the following command:


sudo fdisk -l

---

### Post by mgbolts on 2008-09-19
Thanks for responding.  Is this what you mean. I note that i have not got drive activated in the bios? I will reboot and post this in a minute. 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41495485

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

---

### Post by mgbolts on 2008-09-19
Hi, post with both drives running.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13c03cd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41495485

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30027   241191846   83  Linux
/dev/sdb2           30028       30401     3004155    5  Extended
/dev/sdb5           30028       30401     3004123+  82  Linux swap / Solaris

---

### Post by Titan8990 on 2008-09-19
Alright, now lets see the output of this command:


sudo mount



Edit: I believe I misread your post at first. You currently have the drive working properly but are having speed issues? Is there any particular reason you formatted the drive in NTFS?

---

### Post by mgbolts on 2008-09-19
Output for mount:

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/mgbolts/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mgbolts)


The drive was already formatted. I was using it as a USB external drive until I felt comfortable with the the ubuntu server.  The USB drive was being been plugged into a macbook pro (dual boot OSX and XP) and another couple of xp boxes. I am happy to run with whatever format on the server - but need to access from both mac and windows.

I trust that answers your question.

Cheers

---

### Post by Titan8990 on 2008-09-19
It can be any file type and still be accessed by Windows and MAC clients but if it is EXT3 you would no longer be able to plug it in to your Windows box. EXT3 is the ideal format for Linux drives.

How are you testing the speed of the drive?


Edit: Also, how do you plan to share the drive? SAMBA? WebDAV? SFTP? FTP?

---

### Post by mgbolts on 2008-09-19
Hi, I access the ubuntu server via samba. I presume this means that the format of the drives on the server can be pretty much anything (unix compatable I presume). I note that I dont plan to plug the drive into anything other than the server going forward (assuming the server works ok). The usb thing was just temp. until the server was stable.

On the server itself I ran Iozone (only on the IDE drive so far).  On the mac, I just did a quick and dirty - timed 5 gig file copy. The mac sees the shared folders via samba and that seems to be working well. I have not tried to the xp side yet. I note that I am still trying to get iozone running on the mac (osx).

The difference in performance of the 5gig file copy between the two drives was large. the new stat (sic) drive is around 30% slower (or put another way, the ide is 50% faster).

Hope this helps

---

### Post by Titan8990 on 2008-09-19
Personally, I would give it a shot with a EXT3 reformat. Also, I would use a different protocol that often produces better results. SFTP would be my pick. Very easy to install and get the clients going.

sudo apt-get install ssh-server


No configuration required (unless you are looking to have a server w/o authentication).


For the Windows clients you can use WinSCP. I assume that the MACs come with ssh/scp by default since they are BSD based.

---

### Post by mgbolts on 2008-09-19
Thanks, I will give it go. sounds like another late night!

---

### Post by mgbolts on 2008-09-20
Hi,

I managed to get it running again after reformting to ext3 as you suggested. In summary good outcome. Still uses AHCI though otherwise it wont recognise the sata drive.

Still running Samba at this stage. Will play around later with other server structures.

Simple 5gig copy performance from client mac is now about the same between the two drives, doing about 40mb/s per second. Benchmarked both drives with iozone locally on the server with the old ide getting around 50-55mb/s and the new sata getting around 90mb/s (at levels above caching). I am yet to get iozone running remotely to test the server across the network -> the next job.

So it seems the sata drive is now not going to be a major bottleneck, need to focus on network performance next.

Thanks for your help

Cheers

---

### Post by Shazaam on 2008-09-20
Just a quick note...
I have an older WD 320gig SATA drive that has an actual jumper to set speeds (150/300). Does yours? On the newer drives WD might have removed it.

---

