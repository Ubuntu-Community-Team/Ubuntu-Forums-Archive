---
title: "Incorrect file sizes?"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by d4m1r on 2012-02-19
Hey guys, today I copied 2 video files from my Ubuntu partition to an attached USB stick but I realized Ubuntu is showing an incorrect file size for both files :confused: Both files are 700mb (as confirmed under Windows) but in Ubuntu they are 730mb...It is weird because the USB drive only had 1.4GB of free space left, so despite Ubuntu showing the total file size for both files as 1.46GB, they still both copied over fine....

I only noticed it with video files because I know how large the files should be but I figure other files could be affected as well. Has anyone seen this before or knows how to correct it?

---

### Post by Krytarik on 2012-02-19
Please see this earlier thread:

[http://ubuntuforums.org/showthread.php?t=1861334](http://ubuntuforums.org/showthread.php?t=1861334)

Regards.

---

### Post by llamabr on 2012-02-19
Uh huh.  So navigate in terminal to the place where your videos are, and do a:

```
ls -l filename
```

then

```
ls -lh filename
```

the latter will give you the human readable file size.  I think you'll find that your ubuntu is reporting the correct file size in MB, not MiB

---

### Post by d4m1r on 2012-02-19
> **llamabr said:**
> Uh huh.  So navigate in terminal to the place where your videos are, and do a:

```
ls -l filename
```then

```
ls -lh filename
```the latter will give you the human readable file size.  I think you'll find that your ubuntu is reporting the correct file size in MB, not MiB

Dam you nautilis ](*,)

You'd think with a change like this they'd at least give us the option to display MB or MiB based on personal preference...

---

