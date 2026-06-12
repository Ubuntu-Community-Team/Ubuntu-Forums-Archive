---
title: "cant ssh"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by ben22 on 2008-06-11
hi,

when connecting via ssh to my remote computer i get the following message

```
ben2@ben2-desktop:~$ ssh ben@IP
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
94:75:10:54:d4:1f:66:9d:4e:78:df:7e:59:90:ac:16.
Please contact your system administrator.
Add correct host key in /home/ben2/.ssh/known_hosts to get rid of this message.
Offending key in /home/ben2/.ssh/known_hosts:1
RSA host key for IP has changed and you have requested strict checking.
Host key verification failed.

```
The known_hosts file is not really readable.

Any suggestions what to do to connect?

Thx,
ben

---

### Post by Najand on 2008-06-11
Just open a terminal and remove known_hosts using:
rm /home/ben2/.ssh/known_hosts
and then try again.

---

