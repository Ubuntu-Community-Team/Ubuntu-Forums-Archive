---
title: "Fat32 error ! can not delete files"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Me! on 2008-07-10
Hi

I copy some files to external HD by Live CD of Ubuntu (Arabic File Name)

when I connect HD to Ubuntu System the files name looks Like unknown chars

I restart LiveCD then recopy files , It OK

but I can not delete unkown file names

I can move it only , I can not rename all of them

I repared fat32 with gparted ! but not fixed

how to delete those files ?

Thank you

---

### Post by iaculallad on 2008-07-10
Had you tried to delete this file(s) using their inode number?

To list files with their inode numbers displayed:

```
ls -il
```

To find and delete the file on the current directory when you already know the inode number:

```
find . -inum [inode-number] -exec rm -i {} \;
```

---

