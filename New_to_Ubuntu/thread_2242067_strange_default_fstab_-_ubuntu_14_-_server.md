---
title: "strange default fstab - ubuntu 14 - server"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by bulsatar on 2014-08-30
Morning,
I was looking into a separate issue when I noticed that when I tried to install some new software, the error coming back said disk full.  I thought that strange because the disk said 111gb free when I checked it.  I took a look at my fstab and it looks really different than the one I have on my desktop (mint).  I am thinking that something didn't get mounted correctly or isn't getting mounted.  for instance I don't see /home.  I am not a linux guru, just dabble enough to get by, so any help would be appreciated!

here is my fstab
```
proc            /proc           proc    nodev,noexec,nosuid 0       0/dev/mapper/Soun--Server--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=272245fb-11b7-4fa9-88d6-3d2d046c20db /boot           ext2    defaults        0       2
/dev/mapper/Soun--Server--vg-swap_1     none            swap    sw              0       0
/dev/sdb2       /media/Data_Storage    ext4    defaults    0    2
```

here is what my partitions show (df -h)
```
Filesystem                         Size  Used Avail Use% Mounted on/dev/mapper/Soun--Server--vg-root  109G  6.1G   98G   6% /
none                               4.0K     0  4.0K   0% /sys/fs/cgroup
udev                               483M  4.0K  483M   1% /dev
tmpfs                               99M  752K   98M   1% /run
none                               5.0M     0  5.0M   0% /run/lock
none                               493M  4.0K  493M   1% /run/shm
none                               100M     0  100M   0% /run/user
/dev/sdb2                          1.4T  481G  818G  37% /media/Data_Storage
/dev/sda1                          236M  232M     0 100% /boot



```


what gparted shows is attached in pic.  I have never seen "extended" as a partition.  Like I said, I haven't touched fstab or anything else to do with the partitions besides add in the 2nd harddrive which is just storage.  I would like to avoid wiping out and reinstalling but will if I have to.[ATTACH=CONFIG]255970[/ATTACH]

---

### Post by mcduck on 2014-08-30
Your problems are caused by the separate /boot partition, which is only 236M in size. If any updates include a kernel update, they'll need to be able to add the new kernel files there, and right now that partition is already 100% full. While I'd recommend either getting rid of the separate /boot, or at least increasing it's size, the quick fix is to uninstall some old kernel versions. Running "sudo apt-get autoremove" should be able to do that for you.

What comes to /home partition, Ubuntu's installer doesn't create one for you automatically so if you want /home on a separate partiton instead of the main one, you'll need to set it up ypurself (during the install or afterward).

---

### Post by bulsatar on 2014-08-30
I understand how to increase the size.  /home not being on a separate partition is fine with me since it is a server.  How would I go about getting rid of the separate /boot partition?  Doesn't grub need that?

---

### Post by ajgreeny on 2014-08-30
I think this is a problem of your server using LVM for the root partition at least, if not all of them.  If LVM is chosen (or perhaps used by default in server installs) the installer automatically makes a /boot partition of 256MB, thus causing this problem with lack of space if you do not regularly remove all but the two most recent kernels.

You can see exactly which kernel versions are installed on your system with ```
ls /boot | grep vmlinuz
``` and then remove the unwanted kernels the usual way with apt-get remove.

---

### Post by Bashing-om on 2014-08-30
bulsatar; Hi !

In addition, there is an active bug report in respect to the /boot partition created too small:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

I have seen a request on this forum for those affected to add their voice to the report.

Just my bit
[INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by bulsatar on 2014-08-30
I added myself for the affects me and will keep this thread bookmarked so I can remember this for when it happens again.  Thanks for help!

---

### Post by bulsatar on 2014-09-07
Just as a followup, I reinstalled ubuntu on my server and used a normal setup (ie. no LVM).  It was causing other errors and pileup in the root directory.  It was such a hassle to change partition sizes that I just gave up.

For others that happen across this:   _**LVM is not for beginners!!!!!**_

---

### Post by cariboo on 2014-09-08
> **bulsatar said:**
> Just as a followup, I reinstalled ubuntu on my server and used a normal setup (ie. no LVM).  It was causing other errors and pileup in the root directory.  It was such a hassle to change partition sizes that I just gave up.

For others that happen across this:   _**LVM is not for beginners!!!!!**_

Just to add to this, LVM isn't really needed for a system with only a single storage device. It works great with multiple storage devices. As with everything Linux, it helps if you know what you are doing. :)

---

