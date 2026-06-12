---
title: "error: attempt to read or write outside of disk 'hd0'"
date: 2015-02-04
forum: New to Ubuntu
---

### Post by 118118 on 2015-02-04
I have this when trying to boot to windows or ubuntu.

I don't need to save the computer, it was falling apart etc.. But I do wish to save some of the files. It seems that I have access to them, because I can boot up a command line and the ls command lists the documents I need to save.

I tried mounting a flash drive in order to transfer them to a second computer, but using mount I am told that I can't because the system is read only.

Any help would be great.

---

### Post by 118118 on 2015-02-05
bump

---

### Post by Bashing-om on 2015-02-05
118118; Hello;

One can always use a liveDVD(USB) to copy off the files from the install .. no biggy.

If ya want to investigate the partitioning of the hard drive(s); post back the outputs of terminal commands:
```

sudo fdisk -lu
parted -l

```

Look at the numbers
[INDENT][INDENT][INDENT]see what tale gets told
[/INDENT][/INDENT][/INDENT]

---

