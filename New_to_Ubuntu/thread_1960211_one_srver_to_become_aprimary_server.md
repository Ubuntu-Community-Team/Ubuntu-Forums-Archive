---
title: "one srver to become aprimary server"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by wiqi5 on 2012-04-17
I installing and configuring a drbd on both servers and restart the drbd before it i mount the disk /dev/sdb1 on a /home. /dev/sdb1 is a disk on both servers that on both servers. now when i trying to assign a primary role to one server i-e is drbdadm primary r0 it give me a error "cannot change the state.refusing to become a primary without atleast one uptodate disk" similar error occur when i write a command drbdadm -- --overwrite -data-of-peer-primary all. please help me out i am very embarrassing due to this error.
thanks

---

### Post by callmemahavir on 2012-04-17
Have you tried the documentation given in the url...

[http://www.drbd.org/users-guide/ch-admin.html](http://www.drbd.org/users-guide/ch-admin.html)

Entire docs are available at ...

[http://www.drbd.org/users-guide/](http://www.drbd.org/users-guide/)

---

