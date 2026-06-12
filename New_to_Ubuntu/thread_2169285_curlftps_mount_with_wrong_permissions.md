---
title: "curlftps mount with wrong permissions"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by zdxsKXK on 2013-08-21
hi.

im trying to mount a ftpshare using curlftps command like:

me@home:~$ mkdir mountdir
me@home:~$ curlftps user:passwd@ftpserver mountdir     <<<< mount everything as root

me@home:~$ curlftps user:passwd@ftpserver mountdir -v -o uid=1000,gid=1000   <<< mount as right owner but

still can not copy anything because of wrong permissions
drw-rw-rw- 1 me me 0 May 21 11:11 Data/

any other attempt using nautilus etc. worked fine.
thanks for any help

best regards

---

