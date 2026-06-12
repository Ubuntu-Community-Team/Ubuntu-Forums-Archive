---
title: "Trouble installing OSS :("
date: 2008-07-17
forum: New to Ubuntu
---

### Post by f00sh on 2008-07-17
the file is in my home dir

```
f00sh@f00sh-desktop:~$ sudo dpkg -i oss-linux_v4.0-1016_i386.deb
[sudo] password for f00sh: 
dpkg: error processing oss-linux_v4.0-1016_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux_v4.0-1016_i386.deb
f00sh@f00sh-desktop:~$ 
```

can anyone help?

---

### Post by f00sh on 2008-07-17
> **f00sh said:**
> the file is in my home dir

```
f00sh@f00sh-desktop:~$ sudo dpkg -i oss-linux_v4.0-1016_i386.deb
[sudo] password for f00sh: 
dpkg: error processing oss-linux_v4.0-1016_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux_v4.0-1016_i386.deb
f00sh@f00sh-desktop:~$ 
```

can anyone help?

problem solved :) for anyone else experiencing this problem in the command change the 'linux_v4.0' to 'linux-v4.0' 

(:

thanks

---

### Post by arpanaut on 2008-07-17
Sensitive little buger that command line!

Uh-Huh Uh-Huh
:biggrin:

---

