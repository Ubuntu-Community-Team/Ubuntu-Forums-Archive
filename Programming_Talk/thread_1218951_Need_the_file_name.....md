---
title: "Need the file name...."
date: 2009-07-21
forum: Programming Talk
---

### Post by veda87 on 2009-07-21
whenever I switch from graphical environment to any one of the virtual console... it will prompt like ```
ubuntu 8.10 veda-desktop tty1

veda-desktop login:
``` I knew that ```
ubuntu 8.10 veda-desktop tty1
``` is present in the file /etc/issue.... 

I wanted to know in which file ```
veda-desktop login:
Password:
```

Can anyone tell me the name of the file....

and where is the Last login details are been stored...

---

### Post by iponeverything on 2009-07-21
> **veda87 said:**
> whenever I switch from graphical environment to any one of the virtual console... it will prompt like ```
ubuntu 8.10 veda-desktop tty1

veda-desktop login:
``` I knew that ```
ubuntu 8.10 veda-desktop tty1
``` is present in the file /etc/issue.... 

I wanted to know in which file ```
veda-desktop login:
Password:
```

Can anyone tell me the name of the file....

and where is the Last login details are been stored...

> veda-desktop

is coming from /etc/hostname

```
login:
Password:
```

are coming from the /bin/login binary -- they are hard coded.

run the command "last" to see previous logins.

---

