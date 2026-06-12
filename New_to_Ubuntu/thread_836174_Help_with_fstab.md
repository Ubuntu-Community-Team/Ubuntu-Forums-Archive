---
title: "Help with fstab"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by xXxWandererxXx on 2008-06-21
I'm bit new in Linux, and I want to have all privileges to my files on filesystem. It seams that my files are RO, and I want to do everything that I want with them so I need to change them to RW, I did some searching about this and I found that fstab is for that, but I'm not sure how that would look properly. Can anybody help me?


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0fbde73f-3811-4705-9d72-70ab9db5eedf /               ext3    relatime,errors=remount-rw 0       1
# /dev/sda1
UUID=f11e2f9c-f1c7-40e3-afac-02e38d177044 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Ub1476 on 2008-06-21
Hi, I think fstab just defines what voumes to mount when the system starts, so you don't have to edit that.

However, haveing RW acces to every file and directory on the system is serious security issue. It shouldn't be much of a problem to just use sudo. For instance, if you need to change some files in /etc/X11, just press Alt+F2 and write "sudo nautilus". This will open nautilus (the filebrowser) in root (administrator) mode, and grant you all access. You can also use the terminal. Like, if you want to remove a file (not reccomended though), put "sudo" in front of the command:

```
sudo rm /var/log/file
```

Again, no-one should have root acces throught an entire session.

---

### Post by xXxWandererxXx on 2008-06-21
I agree, but I installed something, and now I can't remove it because I don't have privileges... I tried sudo nautilus, and it won't start nautilus, when I type in just nautilus it starts normal

---

### Post by Ub1476 on 2008-06-21
Try to type "sudo nautilus" from the terminal. 

Also what did you install and how did you do it?

---

### Post by the_doc on 2008-06-21
Better to use..

gksudo nautilus 

..for gui apps.

---

### Post by xXxWandererxXx on 2008-06-21
Hamachi.... I used some instructions... And it worked fine, but I did something wrong in joining session of hamachi and it blocked, and afterwards it was always on. So Im tring to delete it manual

---

### Post by xXxWandererxXx on 2008-06-21
Finaly, that's what I wanted.. Thx

---

### Post by bodhi.zazen on 2008-06-21
See also :

[uwiki]RootSudo[/uwiki]

and

[uhelp]community/FilePermissions[/uhelp]

---

### Post by WitchCraft on 2008-06-21
> **xXxWandererxXx said:**
> I'm bit new in Linux, and I want to have all privileges to my files on filesystem. It seams that my files are RO, and I want to do everything that I want with them so I need to change them to RW, I did some searching about this and I found that fstab is for that, but I'm not sure how that would look properly. Can anybody help me?


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0fbde73f-3811-4705-9d72-70ab9db5eedf /               ext3    relatime,errors=remount-rw 0       1
# /dev/sda1
UUID=f11e2f9c-f1c7-40e3-afac-02e38d177044 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

login as root

to enable the root account: sudo passwd

---

### Post by bodhi.zazen on 2008-06-21
> **WitchCraft said:**
> login as root

to enable the root account: sudo passwd

Setting a root password and logging is a root is not the best of advice to give to new users and it is best to teach them how to use sudo and permissions. If you want to post how to enable the root account you should include advice re re-locking root at a later time as well as appropriate cautions.

If you are an experienced user you are of course free to run your box the way you like, but on the Ubuntu forums we have a fair number of new users and it is a disservice to them to give this kind of advice.

[New forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201") 

If you log in as root there are security implications and *hopefully* protection of system files form inadvertent whimsical changes -> breakage.

You should learn to use sudo and gksu (kedsu on KDE) + permissions.

To lock the root account (if you set a password)

```
sudo passwd root -l
```

---

