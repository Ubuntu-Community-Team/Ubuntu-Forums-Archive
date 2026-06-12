---
title: "If I copy a 74 bytes file 100,000 times, how much free space will it require?"
date: 2009-11-13
forum: Programming Talk
---

### Post by dE_logics on 2009-11-13
??

51mb?

---

### Post by kayosiii on 2009-11-14
Depends on the filesytem and filesystem configuration... Only one filesystem I know of uses only the amount of space needed for a file (it is available for linux but not in the kernal proper nor likely will be).

Usually it will be the minimum filesize * 100,000... where minimum filesize will be something like 4k.

Hope that helps...

---

### Post by dE_logics on 2009-11-14
Yes, that was the issue....thanks.

---

### Post by kayosiii on 2009-11-17
I just found news that very unexpectedly the filesystem that I mentioned may in fact go into the mainline kernel in 2010... So if you need to create stupid amounts of small files and can't find another way around the problem then maybe take a look at reiser4 filesystem.

---

