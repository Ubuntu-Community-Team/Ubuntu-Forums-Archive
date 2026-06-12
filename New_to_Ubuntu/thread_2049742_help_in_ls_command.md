---
title: "help in ls command"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by rraj.be on 2012-08-29
Hi everyone,

Can any one please explain how to interpret these output?

like what is total, what is 0 in it,

drqxr-xr-x 
2,15,1,1,1, 
root root,

100, 4289

and why 253,0,1,2 etc, and the next is date and time of modification or creation and what is the last 4 numbers for character devices alone?

If i can get a generic detailed answer, It would be helpful and its a question from many of my friends too.

```
./bsg:
total 0
drwxr-xr-x  2 root root    100 Aug 29 16:32 ./
drwxr-xr-x 15 root root   4280 Aug 29 16:32 ../
crw-------  1 root root 253, 0 Aug 29 08:53 0:0:0:0
crw-------  1 root root 253, 1 Aug 29 08:53 4:0:0:0
crw-------  1 root root 253, 2 Aug 29 08:53 5:0:0:0
```

Thanks a lot in advance.

---

### Post by Pand5461 on 2012-08-29
total 0 - size in kilobytes (not sure if it's for loose files or including the files in folders)

File permissions:
[INDENT]first letter[/INDENT]
    [INDENT][INDENT]- for ordinary files
    d for directory
    c for character device (like *tty*s, /dev/null etc.)
    b for block device (like disks)
    l for links
    p for pipes
    s for sockets[/INDENT][/INDENT]
  [INDENT]permissions[/INDENT]
    [INDENT][INDENT]r user can read it
    w user can write to it
    x user can execute it/browse folder
    - the permission is unset[/INDENT][/INDENT]

There are 9 letters for permissions: 3 for the owner of the file, for the group the owner is in and for others. So, drwxr-xr-x means a directory with full permissions to owner, and read and execute permissions to the group and to others.

Next, a number is the number of directory entries (1 for a regular file, >1 for a directory)

Next, owner and group, size in bytes (or device numbers), date of modification and filename.

---

