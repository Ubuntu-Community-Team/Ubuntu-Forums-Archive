---
title: "Access for second user to NTFS partition"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by muldengold on 2015-01-19
Hi,

I made a fresh install of ubuntu 14.04. I have full access to my secondary hdd which is NTFS. The problem ist: the second user on the ubuntu installation can't access this hard disk. I tried to change permission using gksu nautilus -> permissions. Under "Others" "Access" it says "Create and delete files", But still doesn't work. I also tried sudo chmod 755 -R /media/... - doesn't work either. Any help would be very welcome!

Sandro

---

### Post by vinnywright on 2015-01-19
is the NTFS drive always mounted as it's in /etc/fstab or plugged in as kneaded ,,,,,,,,,if plugged in as kneaded the user should be able to access it if they are in the   "plugdev"  group.

if always mounted their should be 1 more directory under /media that needs to be checked for permissions   /media/<where you mounted it> 

VINNY

---

### Post by yancek on 2015-01-19
Linux permissions using chmod won't work on ntfs partitions.  You need to investigate umask, dmask and fmask options or post  what permissions you want for which users and someone may be able to make a suggestion.

---

### Post by muldengold on 2015-01-20
Thanks for the help! The solution was that the hard disk was mounted under /media/myname (myname could not be accessed by other useres I guess) AND I had to edit the /etc/fstab 

For this I created a folder in media named "data" -> sudo mkdir /media/data (here will the drive be mounted from now on)
Then edited the fstab using gedit -> gksu gedit /etc/fstab 

and changed in the line for my drive /media/myname to /media/data like this:

#Entry for /dev/sdb1 :
UUID=406DEA9A6D426EFF	/media/data	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0

That was all.

I hope this also works for others!

Best wishes 
Sandro

---

