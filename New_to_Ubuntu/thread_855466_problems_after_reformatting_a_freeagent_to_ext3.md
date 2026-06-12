---
title: "problems after reformatting a freeagent to ext3"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by nekroskoma on 2008-07-10
today i got a freeagent external hd and decided to reformat it to ext3

now it seems i cannot write to it with out being root

i'm guessing it permission are screwed up since the permissions property tab says "permissions of "Disk" could not be determined"

scratch that i can write to it though the rest still applys, how can i fix the permissions thing

---

### Post by DGortze380 on 2008-07-10
to change the permission on the drive you need to first find where it is mount. It's probably in:
/media/myDrivesName  (replace myDrivesName with the name of your drive, obviously).

Make sure you're the owner. To check this

ls -al /media

If you're not the owner:

chown userName /media/myDrivesName

so to change permissions for this drive just:

chmod 700 /media/myDrivesName

This give the owner full access and everyone else (except root) has no access.


Sidenote:
    I went through two of those drives before a ditch seagate completely and bought a maxtor.  The drives work fine out of the box, but once I formatted two partitions (hfs+ and fat32) they would never mount correctly.

---

### Post by nekroskoma on 2008-07-11
> **DGortze380 said:**
> to change the permission on the drive you need to first find where it is mount. It's probably in:
/media/myDrivesName  (replace myDrivesName with the name of your drive, obviously).

Make sure you're the owner. To check this

ls -al /media

If you're not the owner:

chown userName /media/myDrivesName

so to change permissions for this drive just:

chmod 700 /media/myDrivesName

This give the owner full access and everyone else (except root) has no access.


Sidenote:
    I went through two of those drives before a ditch seagate completely and bought a maxtor.  The drives work fine out of the box, but once I formatted two partitions (hfs+ and fat32) they would never mount correctly.
i did that and its fine now but now i have this (screen below) is this some kind of problem or something, it annoys me greatly

---

### Post by DGortze380 on 2008-07-11
> **nekroskoma said:**
> i did that and its fine now but now i have this (screen below) is this some kind of problem or something, it annoys me greatly

not sure why you have that. mount the drive and post the output of ls -al /media

---

### Post by nekroskoma on 2008-07-11
> **DGortze380 said:**
> not sure why you have that. mount the drive and post the output of ls -al /media

```
total 20
drwxr-xr-x  4 root       root 4096 2008-07-11 18:42 .
drwxr-xr-x 21 root       root 4096 2008-06-16 15:23 ..
lrwxrwxrwx  1 root        999    6 2008-05-28 12:11 cdrom -> cdrom0
drwxr-xr-x  2 root        999 4096 2008-05-28 12:11 cdrom0
-rw-r--r--  1 root       root   61 2008-07-11 18:42 .hal-mtab
-rw-------  1 root       root    0 2008-07-11 15:20 .hal-mtab-lock
drwx------ 77 nekroskoma root 4096 2008-07-10 22:28 satori

```

the same thing happens when i mound my flash drive but i hardly ever use my flash drive to begin with

---

### Post by DGortze380 on 2008-07-12
> **nekroskoma said:**
> ```
total 20
drwxr-xr-x  4 root       root 4096 2008-07-11 18:42 .
drwxr-xr-x 21 root       root 4096 2008-06-16 15:23 ..
lrwxrwxrwx  1 root        999    6 2008-05-28 12:11 cdrom -> cdrom0
drwxr-xr-x  2 root        999 4096 2008-05-28 12:11 cdrom0
-rw-r--r--  1 root       root   61 2008-07-11 18:42 .hal-mtab
-rw-------  1 root       root    0 2008-07-11 15:20 .hal-mtab-lock
drwx------ 77 nekroskoma root 4096 2008-07-10 22:28 satori

```

the same thing happens when i mound my flash drive but i hardly ever use my flash drive to begin with

That's odd. The permissions look fine, I couldn't tell you why it's showing up like that. Personally, if it were me, I wouldn't worry about it. If it works, and its showing up correctly in the terminal, I'd consider it fine.

That's just me though. If it bothers you, I'm sure you can find an answer somewhere. Perhaps someone here knows why? Good luck!

---

### Post by bumanie on 2008-07-12
It could be a firmware issue where the drive does not understand ext3 filesystem. I have read about problems with the freeagent and ubuntu. When owners asked seagate about it, they were told, "We don't support linux". Agree with the above, if works, don't worry about the error message.

---

