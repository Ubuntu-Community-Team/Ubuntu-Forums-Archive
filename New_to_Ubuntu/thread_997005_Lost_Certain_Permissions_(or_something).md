---
title: "Lost Certain Permissions (or something)"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by USR612 on 2008-11-29
Hi,
I've been using Ubuntu for all my basic computer needs for over a year now.  I had my Windows partition mounted and shortcuts placed on the desktop.  I logged in yesterday to find the icons were missing and a message that told me I lacked permission when I tried to mount the drives as I had before.  Vista has been not working for me lately, but as I primariy use Ubuntu I don't really care, but I was wondering if it could be due to something wrong on my Windows partition.  Even then, I don't see why I can't mount the shared partition I also have.
Thanks!

---

### Post by taurus on 2008-11-29
If there is something wrong with your windows, ntfs, then you probably need to use the force option to mount it.  Therefore, clicking the drive to mount it won't work.

Assuming your ntfs partition is /dev/sda1, you can try to mount it from a terminal with

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
df -h
```

---

### Post by USR612 on 2008-11-29
Thanks!
Worked perfectly for the windows partition.  I won't worry about the shared partition as it has nothing on it, and I can't remember what I mounted it as before.
Thanks again!

---

### Post by taurus on 2008-11-29
You should start backing up important files on that ntfs partition while you still have a chance  because the force option will not work all the time.  It will work up to a certain point and then it won't even let you do it.

---

