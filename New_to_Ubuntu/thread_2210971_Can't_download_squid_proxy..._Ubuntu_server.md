---
title: "Can't download squid proxy... Ubuntu server"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by James_Kingdom on 2014-03-13
Hey everyone!
I can't seem to install squid... It just says
Do you want to continue so i put y then it says
Err temporary failure resolveing security.ubuntu.com 
The computer is connected to the network and installed stuff about 5 minutes ago.
It said temporary so... I did it today instead of yesterday.

I can't seem to install anything or download! It just says this as a spam:

Err failure resolveing archive.ubuntu.com and security.ubuntu.com THen failed to fetch!
Help pelase...

Any help?
Thanks!

---

### Post by SeijiSensei on 2014-03-13
Looks like a DNS problem to me.  Both those hostnames resolve correctly for me.

```

Seiji@GhostWorld:~$ host archive.ubuntu.com
archive.ubuntu.com has address 91.189.91.14
archive.ubuntu.com has address 91.189.91.15
archive.ubuntu.com has address 91.189.92.200
archive.ubuntu.com has address 91.189.92.201
archive.ubuntu.com has address 91.189.88.149
archive.ubuntu.com has address 91.189.91.13
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::18
archive.ubuntu.com has IPv6 address 2001:67c:1360:8c01::19
archive.ubuntu.com has IPv6 address 2001:67c:1360:8001::17

Seiji@GhostWorld:~$ host security.ubuntu.com
security.ubuntu.com has address 91.189.92.201
security.ubuntu.com has address 91.189.88.149
security.ubuntu.com has address 91.189.91.13
security.ubuntu.com has address 91.189.91.14
security.ubuntu.com has address 91.189.91.15
security.ubuntu.com has address 91.189.92.200
security.ubuntu.com has IPv6 address 2001:67c:1562::14
security.ubuntu.com has IPv6 address 2001:67c:1562::15
security.ubuntu.com has IPv6 address 2001:67c:1360:8001::17
security.ubuntu.com has IPv6 address 2001:67c:1360:8c01::18
security.ubuntu.com has IPv6 address 2001:67c:1360:8c01::19
security.ubuntu.com has IPv6 address 2001:67c:1562::13

```

---

