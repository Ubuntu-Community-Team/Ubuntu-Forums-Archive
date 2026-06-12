---
title: "AVI problem"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by vagelism on 2012-09-23
Hello to all.
I noticed this problem many times and I would like to know if there is any solution.
So when I mount ISO files and try to watch some AVI files I got vlc errors.
If I copy and paste the same files from the mounted ISO files to any folder of my pc then VLC plays them great!
Isn't it strange?
Any solution for that?

---

### Post by vagelism on 2012-09-23
Using fuseiso works without problems.

```
mkdir test
fuseiso test.iso test
```
Now you can play your file from the directory. Clean up afterwards:

```
fusermount -u test
rmdir test
```

---

