---
title: "Did I Partition properly?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by tommyfeds on 2008-04-30
Hi All,

After trying Ubuntu for the first time last week (7.04) I decided to install 8.04 fresh only this time use a separate partition for my home directory. During the install it seemed easy enough to figure out how to partition the drive. (60GB hdd in an HP nc6230) I gave about 18gb to the root drive (/) roughly 38gb for the home (/home) and about 512mb for swap space. 

I had assumed (I know, I know) that since I labeled the partition as /home during the install, that the home directory would be places there. It looks like there is used space on the /home partition, however, it is looking like my data is on the root partition according to line 6 here? 

How can I make sure that my data is on the separate partition in the event I want to re-install the OS fresh?

OH, I installed KDiskFree to get the screen you see below.

Thanks all for any help. 
TommyFeds

[IMG]http://i20.photobucket.com/albums/b214/tommyfeds/Screenshot-KDiskFree.png?t=1209576322[/IMG]

---

### Post by louieb on 2008-04-30
Just wondering what is kDiskFree  did not see it in the repository.?

anyway please list your mount points by running  the** mount **command from a terminal widow.

---

### Post by tommyfeds on 2008-05-01
Hi,

KDiskFree is something I found under add/remove... 

Thanks for the response, below is a copy of what you asked. I dont know what any of it means, but I would like to learn. 

Thanks again for any help. Im looking to make life easy if/when I want to install a fresh copy of the OS or if I mess up somethin good :)

tommyfeds@tommyfeds-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/tommyfeds/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tommyfeds)
tommyfeds@tommyfeds-laptop:~$

---

### Post by louieb on 2008-05-01
```

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda5 on /home type ext3 (rw,relatime)

```Basically mount just list your partitions. The above from your mount command shows / and /home are on different partitions. You look fine there.
```

gvfs-fuse-daemon on /home/tommyfeds/.gvfs type fuse.gvfs-fuse-daemon

```I don't know about this one. Its something new with Hardy I have /home on a separate partition. 
It shows up on my laptop running Hardy. But does not get listed when I run the the mount command on my desktop which is running Gutsy.
Guess I'll go Google the gvfs-fuse-daemon and see what I can find.

Google found this [http://ubuntuforums.org/showthread.php?t=748778](http://ubuntuforums.org/showthread.php?t=748778)

It is something new in Hardy something to do with Disk usage or network sharing. Can't tell which. Anyway I am going to turn it off.

---

### Post by tommyfeds on 2008-05-05
I feel a little better knowing I did it right. 

Thanks again, 
Tommy

---

