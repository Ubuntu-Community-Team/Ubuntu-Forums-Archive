---
title: "some problems about mounting harddisks"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Padrhino on 2008-08-02
hi, i'm a total newbie at ubuntu and i hope this is the right place to ask this question.

In my pc i have 3 partitions. 1 for XP, 1 for ubuntu hardy, 1 for music, movie etc.

I mount this storage partiton with '/' and i don't know what will be the results.

Now i couldn't access this partition. 'mount_point cannot contain the following characters: newline ,G_Dir_Seperator(usually /)'

In my case it is absolutely '/' character. How can i solve this problem?

Thanks...

---

### Post by Diabolis on 2008-08-02
In Linux you can't mount into this place "**/**" because it is where the root directory will be mounted. You'll have to choose another mounting point.

---

### Post by Titan8990 on 2008-08-02
You are having problems because there is already your main filesystem mounted on /. It is customary to mount your partitions somewhere in the /media directory.

---

### Post by Diabolis on 2008-08-02
Yep, or in the **/mnt** directory. Both are the same thing, except that if you mount it in the /**media** directory, an icon of the partition will appear on your desktop.

---

### Post by Padrhino on 2008-08-02
thank you for replies. but i couldn't access where i set mount point to '/' this partition. Can i reset the mount point to what you said via another setting or terminal?

---

### Post by Diabolis on 2008-08-02
Mount points are managed from the fstab file.
```
sudo gedit /etc/fstab
```

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

You can make any changes there, once you are done. Try to mount the drive.
```
sudo mount "mount point"
```

---

### Post by Padrhino on 2008-08-02
ok, with your help i've managed to solve problem...

---

