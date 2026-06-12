---
title: "Python FUSE getattr"
date: 2007-01-09
forum: Programming Talk
---

### Post by 3rdalbum on 2007-01-09
I'm trying to write a FUSE wrapper to the hfsutils package. Hfsutils is a set of command-line programs that let you mount, copy, delete, etc to and from an HFS filesystem.

I'm writing it in Python, from a template I found online.

The bit I'm getting stuck on is the getattr function. It seems to be called in my Python script every time I try to "ls" in my mounted FUSE filesystem. The thing is, I have no idea what should be returned, and in what format or order. The only clue I have is this comment from the template:

```
       - st_mode (protection bits)
        - st_ino (inode number)
        - st_dev (device)
        - st_nlink (number of hard links)
        - st_uid (user ID of owner)
        - st_gid (group ID of owner)
        - st_size (size of file, in bytes)
        - st_atime (time of most recent access)
        - st_mtime (time of most recent content modification)
        - st_ctime (platform dependent; time of most recent metadata change on Unix,
                    or the time of creation on Windows).
```

I can't get any of that information except for "device", so I'm completely lost.

This getattr thing seems to be blocking me, as all operations on the FUSE filesystem fail silently except for mounting and unmounting.

My entire code is here: [http://code.google.com/p/coplandppc/wiki/FuseHfsCode](http://code.google.com/p/coplandppc/wiki/FuseHfsCode)

---

