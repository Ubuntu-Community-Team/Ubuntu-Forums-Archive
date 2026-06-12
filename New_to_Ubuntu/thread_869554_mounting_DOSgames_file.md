---
title: "mounting DOSgames file"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Joshfan on 2008-07-24
i went though the tut on dosbox and i tried mounting my dosgames file but it say i have to do it through root how do i login as root?


[IMG]http://img292.imageshack.us/img292/1647/475869vz3.png[/IMG][http://counter.li.org/]("http://counter.li.org/")

---

### Post by dave.com on 2008-07-24
Try this stuff for reference:

```
user:~$ sudo su - (asks for password- enter your password)
root:~$ cd /
root:/$ chroot / /bin/bash
root:~#        (type exit to logout of shell)
root:~# exit
root:~$ exit
user:~$
```

---

