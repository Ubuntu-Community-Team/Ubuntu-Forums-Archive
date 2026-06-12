---
title: "netcat with windows troubles"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by dmitrijledkov on 2008-07-25
Ubuntu Hardy - nc as installed by default
Windows XP SP3 - nc installed using cygwin

Windows Firewall is off =D

When I listen on ubuntu side:

```
nc -l -p 1024 > backup.tar.bz2
```

Windows can scan it and shows that 1024 is open.

When I listen the same way on windows side. Ubuntu can't scan it is sais can't reverse lookup, no ports to connect to.

Both machines are on local wifi network and I address host as e.g. 192.168.1.100

I need to listen on windows and send my backup to it using ubuntuforums wiki BackingupYourSystem/Tar

---

