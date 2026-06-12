---
title: "Ubuntu LiveUSB has default root access?"
date: 2018-12-16
forum: New to Ubuntu
---

### Post by sean772 on 2018-12-16
I had to fun fsck from my bootstick, and it occurred to me that I didn't have to give my super user password to run the file system check as a super user. Is this normal? Where can I find more information about the default permissions that the bootstick is given, and can I change them? Otherwise it seems like a huge security issue.

My machine is 16.04 running on an oldish laptop.

---

### Post by CatKiller on 2018-12-16
Giving no password and giving a widely-publicised default password are exactly equivalent from a security perspective, and the latter simply inconveniences users with no upside.

There is no security if someone has physical access to the machine. If you are concerned, you can encrypt the contents of your hard drives.

---

