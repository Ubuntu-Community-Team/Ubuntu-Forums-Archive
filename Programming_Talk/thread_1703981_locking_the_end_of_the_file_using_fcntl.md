---
title: "locking the end of the file using fcntl"
date: 2011-03-10
forum: Programming Talk
---

### Post by guest_user on 2011-03-10
say I have these values in my flock struct when I call fcntl,
l_whence = SEEK_END;
l_start = 0;
l_len = 1024;

Will the lock start at the end and go backwards or forwards in the file?

---

