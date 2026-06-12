---
title: "[SOLVED] read linux in xp"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by cristo-father on 2008-06-14
If i download files to linux, can i transfer them to xp? how? can i run them?
My OS is Linux mint (Ubuntu based)

---

### Post by talsemgeest on 2008-06-14
Yes you can, you just have to copy them across to your xp partition or drive.

---

### Post by issih on 2008-06-14
This program claims it lets you mount an ext 2 partition, so you could mount the linux drive and drag data off it.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Personally I just set up a fat32 partition to act as swap between the different OS systems, but that is a bit of a kludge I admit

---

### Post by dracayr on 2008-06-14
you can acces your linux partition from xp by installing the [ext2fs driver]("http://www.fs-driver.org/") on windows

dracayr

---

### Post by cristo-father on 2008-06-14
> **talsemgeest said:**
> Yes you can, you just have to copy them across to your xp partition or drive.
Does drag and drop do the job?

---

### Post by Tomatz on 2008-06-14
You can do this from Linux using ntfs3g

or

You can do this from xp using ext2ifs

[http://www.fs-driver.org/](http://www.fs-driver.org/)


Both work flawlessly though ntfs3g is safer IMO ;)

---

### Post by talsemgeest on 2008-06-14
> **cristo-father said:**
> Does drag and drop do the job?
Yep, its as easy as that.

---

### Post by r76 on 2008-06-14
> **issih said:**
> Personally I just set up a fat32 partition to act as swap between the different OS systems, but that is a bit of a kludge I admit

I disagree, I think it's the best way!
EDIT: although I prefer NTFS rather than FAT

Also I used to use fs-driver, but now I use linux-reader, described in [this thread]("http://ubuntuforums.org/showthread.php?t=785529&highlight=linux-reader").

---

### Post by ukripper on 2008-06-14
I would rather save files to ntfs drive and access them from windows

---

### Post by rraj.be on 2008-06-14
Nothing big in this.

I think there is no need for this much big issue.

Just copy or cut your Required file as usual and paste it in NTFS drive.

Now you can acces your file from this drive when you are inside windows.

Just very simple.

---

### Post by Tomatz on 2008-06-14
> **rraj.be said:**
> Nothing big in this.

I think there is no need for this much big issue.

Just copy or cut your Required file as usual and paste it in NTFS drive.

Now you can acces your file from this drive when you are inside windows.

Just very simple.

Yes this is ntfs3g.

8.04 uses it by default ;)

---

