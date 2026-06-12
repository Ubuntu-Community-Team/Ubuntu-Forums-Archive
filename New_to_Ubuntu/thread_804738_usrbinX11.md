---
title: "usr/bin/X11"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by guycr on 2008-05-23
Why are there multiple nested copies of this folder (more than 30) and usr/bin is about 5 gb in size.

---

### Post by guycr on 2008-05-23
I should have mentioned that I'm using hardy 8.04 kernal 2.6.24-16 generic

---

### Post by guycr on 2008-05-23
wow, this is a rocky intro to this forum! The usr/bin file size is in fact about 114 mb

---

### Post by unutbu on 2008-05-23
```
  /usr/bin:
  lrwxrwxrwx  1 root   root           1 2008-01-15 05:14 X11 -> .
```

X11 is a symlink to /usr/bin. So /usr/bin/X11 points to the same location as /usr/bin. The symlink takes up almost no space.

Way back when, people used to put X applications in /usr/bin/X11, and command-line tools in /usr/bin. It appears Ubuntu decided /usr/bin is good enough. But for compatibility with any scripts that might refer to /usr/bin/X11, they use the symlink to trick the computer into finding X apps even if they are referred to using the /usr/bin/X11 path.

---

