---
title: "Problem with Synaptic"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by x4KlV2OI on 2008-04-29
I was booting up synaptic to get VLC media player, but it came up with this error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
I then do exactly what it said but my terminal came up with this problem:
```
blake@blake-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

```
I have gone into Users and Groups and made sure i have all priviledges, but i still can't.

Any help appreciated!:guitar:

---

### Post by kpkeerthi on 2008-04-29
You need to run the command like this
```
**[COLOR="Red"]sudo[/COLOR]** dpkg --configure -a
```

---

