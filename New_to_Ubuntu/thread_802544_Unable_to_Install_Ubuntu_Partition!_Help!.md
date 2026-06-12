---
title: "Unable to Install Ubuntu Partition! Help!"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Darksci on 2008-05-21
So for some reason I can't install 0.o

Heres the error I get:

[IMG]http://img185.imageshack.us/img185/6016/screenshotuo9.png[/IMG]

---

### Post by spiderbatdad on 2008-05-21
Not sure, but generally XP should be defragged...sometimes twice (regardless of whether the tool tells you the volume doesn't need to be defragged) just prior to attempting to install Ubuntu.

---

### Post by zfolwick on 2008-05-21
if you get any real answers let me know. . . I'm on the same thing, except I'm not trying to dual-boot.

my thread is [here]("http://ubuntuforums.org/showthread.php?t=802453")

---

### Post by volkswagner on 2008-05-21
If you have an existing windows and want to keep it, I recommend manual partitioning.

Post the output of

```
fdisk -l
```

---

### Post by phoenix_abhi on 2008-05-21
Why do not use manual partitioning for dual booting ? OOps already replied.

---

### Post by Nubnut on 2008-05-21
My guess is that you're not allowing enough disk space for the Ubuntu build. I've installed 10 Laptop systems for Teachers in the past week, a few of them dual boots. Since you have a 70 Gb Harfd drive why not abort the install for now and try defragging your hard drive in windows. Back up your essential windows files and try the install again, this time allowing around 20 Gb, 10gb for / (root), twice your ram for /swap, and the remaining for /home

I'm fairly new to this myself but hope this helps.

Of course the easiest option is to allow Ubuntu the entire disk and scrap windows but this may not be an option just yet!!

---

### Post by forestpixie on 2008-05-21
> **spiderbatdad said:**
> Not sure, but generally XP should be defragged...sometimes twice (regardless of whether the tool tells you the volume doesn't need to be defragged) just prior to attempting to install Ubuntu.

If after defragging a couple of times you still have problems try turning of the win pagefile and defragging once more, do the install and then turn the pagefile back on

---

### Post by spiderbatdad on 2008-05-22
> **zfolwick said:**
> if you get any real answers let me know. . . I'm on the same thing, except I'm not trying to dual-boot.

my thread is [here]("http://ubuntuforums.org/showthread.php?t=802453")
:lolflag:

---

