---
title: "External hard drive privledges"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by ian52 on 2014-07-16
Hello,

I googled the problem extensively but could not find a solution that worked or I didn't understand what was going on. Please bear with me I have no real experience with Ubuntu I'm converting from a dead Mac.

I have a 350GB external hard drive that I backed up my videos, photos, etc on and now when I try and copy from it I get an error message saying the drive is read only. I need a way to mount the drive as root (I think) but when I tried using sudo Nautilus it still gave me the same error.

Mount reads: 
ian@ian-ThinkPad-X131e:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ian)
/dev/sdb3 on /media/ian/Storage Drive type hfsplus (ro,nosuid,nodev,uhelper=udisks2)
ian@ian-ThinkPad-X131e:~$ 


I then tried the command 
sudo chown -R ian:ian /media/ian/Storage Drive
and got an error because of the space in the name, but thats the name of the drive so I'm not sure how to write that.

Any help would be very appreciated!

-Ian

---

### Post by Vladlenin5000 on 2014-07-16
Hi, welcome.

```
[COLOR=#ff0000]/dev/sdb3[/COLOR] on /media/ian/Storage Drive
```

where in [COLOR=#ff0000]red[/COLOR] is the path you need for that command.

---

### Post by wn1ytw on 2014-07-16
The first problem is the drive is an HFS+ format and Ubuntu reads that  format but not writes it. Ubuntu can R,W FAT32, and EXT4. 

As for the drive name, enclose it in quotes is one solution.

```


  sudo chown -R ian:ian /media/ian/"Storage Drive"


```

---

### Post by wn1ytw on 2014-07-16
also see here [http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os/332317#332317](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os/332317#332317)

---

### Post by yancek on 2014-07-16
> I have a 350GB external hard drive that I backed up my videos, photos,  etc on and now when I try and copy from it I get an error message saying  the drive is read only

It would not matter if it is read-only if you want to copy FROM it, copying TO it would be a different story.

---

### Post by ian52 on 2014-07-17
> **wn1ytw said:**
> The first problem is the drive is an HFS+ format and Ubuntu reads that  format but not writes it. Ubuntu can R,W FAT32, and EXT4. 

As for the drive name, enclose it in quotes is one solution.

```


  sudo chown -R ian:ian /media/ian/"Storage Drive"


```

I did this and it transferred ownership of some of the files but not all of them. Its in te middle of the transfer now so Ill see where we are at in a few hours or maybe tomorrow.

Thanks for the information.

-Ian

---

### Post by ian52 on 2014-07-18
OK so the few files left that I still don't have access to don't matter - problem solved.

Thanks for the help.

-Ian

---

