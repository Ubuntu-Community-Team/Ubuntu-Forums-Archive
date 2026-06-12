---
title: "error"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by waffleturd on 2008-11-13
i was trying to reinstall compiz and this error popped up
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so i used terminal and this popped up

'sam@sam-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege'

do you know how to fix this?

---

### Post by taurus on 2008-11-13
You need to add sudo in front of that command.

```
**sudo** dpkg --configure -a
**sudo** apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

