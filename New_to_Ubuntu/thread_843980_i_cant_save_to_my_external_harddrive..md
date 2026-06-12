---
title: "i cant save to my external harddrive."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-06-29
i reformated to remove my windows partion from my external harddrive. well i formatted in ext2 and ext3 and i cant save anything to it...

the error message i get is..

The folder cannot be copied because you do not have permissions to create it in the destination.

anyone had this issue before

---

### Post by LuisGMarine on 2008-06-29
Try this in terminal:

```
sudo chown -R $USERNAME:$USERNAME /path/to/mount/point
```

Of course substitute $USERNAME for your actual user name.

This should give you the proper permissions to write to the hdd.

-xkill

---

### Post by PatrickMoore on 2008-06-29
> **LuisGMarine said:**
> Try this in terminal:

```
sudo chown -R $USERNAME:$USERNAME /path/to/mount/point
```

Of course substitute $USERNAME for your actual user name.

This should give you the proper permissions to write to the hdd.

-xkill


do you know how i can find the exact file path im still having issues

---

### Post by LuisGMarine on 2008-06-29
Sure,

Type in this command in to terminal and paste the output:
```

cat /etc/fstab
```

You should see something like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=796670dc-ccb3-4214-b791-58a07df0a677 /               ext3    noatime,nodiratime,errors=remount-ro,data=writeback 0 1
# /dev/sda2
UUID=2543e520-fecd-494d-b8d9-cdd6325f6728 /home           ext3    noatime,nodiratime,errors=remount-ro,data=writeback 0 1
[COLOR="Lime"]# /dev/sdb1
UUID=352a1e14-fb8e-44c6-b031-aed273f1a115 /storage        ext3    noatime,nodiratime,errors=remount-ro,data=writeback 0 1[/COLOR]
# /dev/sda5
UUID=a45d76b6-a64a-178f-29a5-20d1431d2f2f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

As you can see all my /deb/sda* are the partitions and their current mount point, this is my first hdd with Ubuntu 8.04

But look at the entry line highlighted in green for my second hdd.

```
# /dev/sdb1
UUID=352a1e14-fb8e-44c6-b031-aed273f1a115 [COLOR="Red"]/storage[/COLOR]        ext3    noatime,nodiratime,errors=remount-ro,data=writeback 0 1
```

Looking at it more closely, highlighted in red is where Linux is telling me the hdd is mounted.  Now you know the path.  

For example sake lets use mine.  Pretend /dev/sdb1 is my external hdd.  It's tell me that it is mounted to a directory called /storage.  Next run the command I told you earlier, with the path.

```
sudo chown -R $USERNAME:$USERNAME /storage
```

Hope this helps!

-xkill

---

### Post by cariboo on 2008-06-29
You may have trouble changing ownership of the mount point seeing as it is mounted in /, change the permissions at least it will work:

```
sudo chown -R 777 /storage
```

Instead of mounting your dive in / it would be much better to use /media eg:

```
/media/storage
```

Jim

---

### Post by LuisGMarine on 2008-06-29
> **cariboo907 said:**
> You may have trouble changing ownership of the mount point seeing as it is mounted in /, change the permissions at least it will work:

```
sudo chown -R 777 /storage
```

Instead of mounting your dive in / it would be much better to use /media eg:

```
/media/storage
```

Jim

That can work too! :)

-xkill

---

