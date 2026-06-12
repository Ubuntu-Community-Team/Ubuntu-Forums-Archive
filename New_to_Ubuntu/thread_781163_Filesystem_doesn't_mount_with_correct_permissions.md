---
title: "Filesystem doesn't mount with correct permissions"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by ElSean on 2008-05-04
Hi, I have a second HDD that I want any user to be able to read/write too.  I put it into /etc/fstab with the following entry:

/dev/hdb1 /media/Data   ext3    rw,user,auto    0    0

It mounts automatically and everything, but only the root can create files, everyone else can only mount/umount and read.  The directory listing shows this problem too:

drwxr-xr-x 7 root root 4096 2008-05-03 23:42 Data


Anyone know what I'm doing wrong?

---

### Post by Kevbert on 2008-05-04
Try:

/dev/hdb1 /media/Data ext3 defaults 0 1

This may help: [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by svk on 2008-05-04
I had a similar issue and would also like to hear about a solution.  I reinstalled Ubuntu and when I remounted one of my data partitions (ext3) after the reinstall, the reported owner of every file was root.  Worse, all the permissions were screwed up.

I hacked a solution by mounting the partition, cd'ing into it, and running:
```
sudo chown -R username:username ./
```

That is, I recursively changed the owner of every file in the partition to be my user account.  Generally, this is probably not a good idea, but I knew that every file in my partition really ought to be owned by me.

Can anyone explain what's going on here? How does Ubuntu decide who owns the files in a partition or an external hard drive?

---

### Post by ElSean on 2008-05-04
I switched it to use defaults and it still does the same.

---

### Post by MrFSL on 2008-05-04
Check your permissions on the mount folder.

---

### Post by ElSean on 2008-05-04
I set the permissions on the mount folder to 777 (read, write, execute for everyone).  When I do an ls -l without the drive mounted it shows this as the permission setting, but as soon as I mount it, the permissions are changed to 755.

---

### Post by bodhi.zazen on 2008-05-04
Mount the partition.

Then use chown and chmod.

```
sudo chown user.users /media/Data
sudo chmod 770 /media/Data
```

in the chown command "user" = you log in name.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by ElSean on 2008-05-04
Should this change to owner stay after unmounting / rebooting?

---

### Post by bodhi.zazen on 2008-05-04
Yes.

---

