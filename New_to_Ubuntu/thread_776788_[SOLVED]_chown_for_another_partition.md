---
title: "[SOLVED] chown for another partition?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by tropdoug on 2008-04-30
I have partitioned my main Ubuntu disk to provide a second ext3 partition for storing files away from the system. 

However I have found that goobox cannot extract music files to a folder on it, as access is denied. I have found that the owner of the partition is listed as "Unknown" and is set at read only. How do I access it in a terminal to change the ownership permissions of the partition., This is what I see in Places, (attached) and I want to automount the 44.7 Gb volume and change its ownership to 'douglas'

Thanks for any help.

---

### Post by talsemgeest on 2008-05-01
The command to change permissions is chmod, but I can't quite remember how to use it to do disks...

---

### Post by deanjm1963 on 2008-05-01
easy fixed

open a terminal window and type the following

sudo chown -R douglas:douglas /partition or drive name

e.g. I have a separate partition for downloads and I do the following

sudo chown -R dean:dean /misc
sudo chmod -R 755 /misc

if you have an external hardrive, check in the "media" folder to see what it's called, e.g. mine is "disk" and if I format that I would type

sudo chown -R dean:dean /media/disk
sudo chmod -R 755 /media/disk

hope this helps

---

### Post by tropdoug on 2008-05-01
Hi Dean

with the numbers, ie 755 I have not yet got to grips with them, so which would I use, to give myself the necessary requirement, to access and read write the disk. 

Thanks

---

### Post by talsemgeest on 2008-05-01
First you need to tell us where the drive is mounted. Is it in /media/disk ?

If that was the case, you would use ```
sudo chown -R douglas:douglas /media/disk
```

---

### Post by tropdoug on 2008-05-01
Yup its /media/disk

```
douglas@desktop:/media$ ls -l
total 40
lrwxrwxrwx  1 root    root        6 2008-04-19 19:40 cdrom -> cdrom0
drwxr-xr-x  2 root    root     4096 2008-04-19 19:40 cdrom0
drwxrwx---  4 douglas douglas  4096 2008-04-15 21:56 disk
drwxr-xr-x 47 root    root    32768 1970-01-01 10:00 seagate

```

Looking at the above I guess I only have to change the  [COLOR=Blue]"drwxrwx---" [COLOR=Black]bit?[/COLOR]
[/COLOR]

---

### Post by talsemgeest on 2008-05-01
So it is definitely disk, not seagate? Because it looks like you have access privileges to disk, but not seagate. If [deanjm1963]("http://ubuntuforums.org/member.php?u=85163") is right, then all you have to do is ```
sudo chown -R douglas:douglas /media/seagate
```

---

### Post by deanjm1963 on 2008-05-01
first you need to give yourself ownership with "chown" - "change owner"

```
sudo chown -R douglas:douglas /media/disk
```

then you need to give yourself read and write permissions with "chmod" - "change mode"

```
sudo chmod -R 755 /media/disk
```

if it's also seagate that you need to access and change permissions, do the above but substitute /media/seagate for /media/disk

---

### Post by talsemgeest on 2008-05-01
I'll have to remember that, I've never really needed to use it before...

---

### Post by tropdoug on 2008-05-01
Thaks [deanjm1963]("http://ubuntuforums.org/member.php?u=85163")

That fixed it. simple really, hope I learn this stuff soon. 

Interestingly I thought I might change the ownership of seagate which is an external drive, but using the same process, it will not allow me to change the ownership. it tries to access the various folders in the tree, and each one returns "Operation not permitted" any ideas why that would be?

---

