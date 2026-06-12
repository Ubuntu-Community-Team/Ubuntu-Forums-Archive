---
title: "Create a file system"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by mosquetero on 2012-07-03
Hi!

I am trying to create a file system in my new hard drive. To do so I used the command:

```
mkfs.ext3 sdb
```

Everything looks correct but then when I type:

```
fdisk -l sdb
```

I get the output: "Disk sdb doesn't contain a valid partition table"

Did the file system creation not work? What else do I have to do?

Thanks

---

### Post by westie457 on 2012-07-03
The syntax of the command is wrong. Take a look at ```
man mkfs
``` for more information.

---

### Post by Cheesemill on 2012-07-03
You need to create a partition first to hold the filesystem.

---

### Post by SlugSlug on 2012-07-03
sudo mkfs.ext3 /dev/sdb1

sdb = the drive it's self,  the 1 = 1st partition on drive

(I'd also use ext4).

Or use gparted for a simple GUI :)

---

### Post by sanderj on 2012-07-03
OP:

You're probably better off with Disk Utility: a GUI to create and format partiton.

So: in the Dash, type "Disk Utility" ...

HTH

---

