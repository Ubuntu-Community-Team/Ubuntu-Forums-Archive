---
title: "[SOLVED] How is a file 's refered inode changed?"
date: 2008-02-09
forum: Programming Talk
---

### Post by fyplinux on 2008-02-09
Hi,

The inode represents a file object in a file system,  each inode contains the metadata of a file, like the ownership and the access time,and also, the reference to the data blocks owned([http://www.angelfire.com/myband/binusoman/Unix.html#inodelist](http://www.angelfire.com/myband/binusoman/Unix.html#inodelist))
etc. 

If a file 's content is changed, the inode could only need to update the access time or modtime, and the references to the data block. But, actually, in Ubuntu 7.10, if a file 's content is updated, it is most likely that the file 's corresponding inode is changed. How's this change applied? what is the mechanism of file saving? I am really confused.

Here is an example
```

ing@ing-desktop:~/Desktop/ee$ stat a.c
  File: `a.c'
  Size: **22959 **          Blocks: 48         IO Block: 4096   regular file
Device: 807h/2055d      Inode: **98133**       Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    ing)   Gid: ( 1000/    ing)
Access: 2008-02-07 19:03:10.000000000 +0000
Modify: 2008-01-26 23:02:01.000000000 +0000
Change: 2008-01-26 23:02:01.000000000 +0000

ing@ing-desktop:~/Desktop/ee$ gedit a.c//one byte was deleted here

ing@ing-desktop:~/Desktop/ee$ stat a.c
  File: `a.c'
  Size: **22958 **          Blocks: 48         IO Block: 4096   regular file
Device: 807h/2055d      Inode: **99899 **      Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    ing)   Gid: ( 1000/    ing)
Access: 2008-02-10 00:10:42.000000000 +0000
Modify: 2008-02-10 00:10:42.000000000 +0000
Change: 2008-02-10 00:10:42.000000000 +0000



```

---

### Post by LaRoza on 2008-02-09
The kernel would do it I believe.

I don't think that applications can have such access to the file system.

---

### Post by stroyan on 2008-02-09
strace knows the answer.
The original inode is still there with a new name.
gedit renamed it and created a new file with the name you checked.
```
$ echo abc > xyzzy
$ stat xyzzy
  File: `xyzzy'
  Size: 4               Blocks: 8          IO Block: 4096   regular file
Device: 805h/2053d      Inode: 63562       Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    mike)   Gid: ( 1000/    mike)
Access: 2008-02-09 18:15:15.000000000 -0700
Modify: 2008-02-09 18:15:15.000000000 -0700
Change: 2008-02-09 18:15:15.000000000 -0700
$ strace -o gedit.strace gedit xyzzy
$ grep xyzzy gedit.strace 
execve("/usr/bin/gedit", ["gedit", "xyzzy"], [/* 37 vars */]) = 0
open("/home/mike/xyzzy", O_RDONLY)      = 15
lstat64("/home/mike/xyzzy", {st_mode=S_IFREG|0644, st_size=4, ...}) = 0
open("/home/mike/xyzzy", O_WRONLY|O_CREAT|O_EXCL, 0666) = -1 EEXIST (File exists)
open("/home/mike/xyzzy", O_RDWR)        = 15
lstat64("/home/mike/xyzzy", {st_mode=S_IFREG|0644, st_size=4, ...}) = 0
rename("/home/mike/xyzzy", "/home/mike/xyzzy~") = 0
rename("/home/mike/.gedit-save-Z8KU5T", "/home/mike/xyzzy") = 0
lstat64("/home/mike/xyzzy", {st_mode=S_IFREG|0644, st_size=3, ...}) = 0
open("/home/mike/xyzzy", O_RDONLY|O_LARGEFILE) = 17
lstat64("/home/mike/xyzzy", {st_mode=S_IFREG|0644, st_size=3, ...}) = 0
$ stat xyzzy
  File: `xyzzy'
  Size: 3               Blocks: 8          IO Block: 4096   regular file
Device: 805h/2053d      Inode: 1034083     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    mike)   Gid: ( 1000/    mike)
Access: 2008-02-09 18:15:49.000000000 -0700
Modify: 2008-02-09 18:15:49.000000000 -0700
Change: 2008-02-09 18:15:49.000000000 -0700
$ stat xyzzy~
  File: `xyzzy~'
  Size: 4               Blocks: 8          IO Block: 4096   regular file
Device: 805h/2053d      Inode: 63562       Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/    mike)   Gid: ( 1000/    mike)
Access: 2008-02-09 18:15:15.000000000 -0700
Modify: 2008-02-09 18:15:15.000000000 -0700
Change: 2008-02-09 18:15:49.000000000 -0700

```

---

