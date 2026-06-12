---
title: "Can home/videos be moved to new partition/hard drive"
date: 2017-04-19
forum: New to Ubuntu
---

### Post by crip720 on 2017-04-19
I just got a new large USB3 hard drive.  Would like to move parts of /home from various Ubuntu installs to it and be able to access it has needed.  Do not want to move /home or used it for backups.  Would like to know best way to prepare hard drive(should I install a distro to it) and how to copy/move sections of /home(s) to it?  These will be large GBs of data/videos.  I know how to copy/move single files, but would like to know if there is a way of moving/copying sections of home like videos or documents/downloads/pictures.  Would also like to access them easily from the Ubuntu that I am using at the time. Have been trying to google this, but most of the returns deal with moving the complete home.  Thank you.

---

### Post by Dennis N on 2017-04-19
Is the new drive for data only (that is, your files, and no OS)? Then you just need to create a partition table with gparted (I suggest using gpt partitioning), and at least one ext4 partition for the folders and files. No OS needs to be installed.

You can mount the drive at startup by adding a line in /etc/fstab. Do that for each Linux OS that is going to access the new drive. If you do this, be sure the drive is plugged in when you turn on your computer. Or you can mount it manually each time from the file manager's side pane.

For access, you can bookmark locations on the drive, or you can make symbolic links to the new folder locations (after moving the contents, of course) on the new drive so that all access is redirected.

---

### Post by Bucky Ball on 2017-04-20
As above. Create a new partition on the new drive, drop your data in it, delete the replicated data in /home.

I don't have any personal data on /home (along with other users). I have the OS running on a 128Gb SSD and everything is on a large /data partition on a 1Tb HDD. The /home folder is still in the / partition on the OS on SSD, but inside that are symlinks to the actual personal data on /data. 

This way, if your install breaks or for some reason you need to reinstall, your personal data is on a totally different partition on a totally different drive. 

If you are running your OS from an SSD, strongly suggest you also put your /swap partition on the HDD. Good luck.

---

### Post by crip720 on 2017-04-20
Thank you for your answers, will try today and let you know if I need any more help.

---

### Post by lisati on 2017-04-20
Tip: if you've got the time and patience, copy/replicate first, and only delete original if you're satisfied that the copy worked.

---

### Post by crip720 on 2017-04-20
Did what you suggested,but had to google to change permissions.  It is working now, but might have made an error changing permissions.  Used this command 'cd /media/your username and sudo chown -R -v your_username:your_username *'.  Think might have change permission for everything on my multi-boot system, was a lot lines going fast and notice some with other kernels/partition names.  I am the only user, so do I need to change back and how?  Have not rebooted yet incase.  The name of the new hard drive/partition is 'def76f98-84df-4505-a0a9-1296adce7e74 and located at /media/username'.  All username are replaced with my own username. Thank you.

---

### Post by Bucky Ball on 2017-04-20
Hmm. Interesting. Would have thought the partition should be mounted at /media/username/data, where 'data' is the name of the mount point you created for the new partition. :-k

---

### Post by crip720 on 2017-04-20
Question is this bad for a single user(as in breaking/borking things) or will everything be okay?  If bad, can you supply code to change back.  Partition name is data and mount point is /media/crip/def76f98-84df-4505-a0a9-1296adce7e74 according to gparted.  Can I change mount point to /media/crip/data safely?  Thank you.

---

### Post by yancek on 2017-04-20
Do you have a directory 'data' in /media/crip?  Partitions on external drives are usually available under the /media/username directory for access.  If you are going to have another drive permanently attached and want it mounted on boot, put an entry in the /etc/fstab directory.  Generally, external drive partitions were placed in the /mnt directory but it doesn't really matter.  Basically, you can do it at either mount point, your choice.  

If you have a data partition under /media/crip, the chown would be more like this run from the /media/crip directory:

> sudo chown -R crip:crip data

You can use other parameters/options if you want.

---

### Post by crip720 on 2017-04-22
I am going to mark this as solved, because I got what I wanted(I hope).  I am glad that I do not have to worry about updating/upgrading an OS.  I am copying some stuff over now, and will see if everything works before deleting.  To Yancek, my data partition in media comes up as the def..., tried to changed it to data in gparted, but did not seem to stick.  Will open other post if I have any problems popup from problem in post #6 and #8.  Thank you for your help.

---

