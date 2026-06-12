---
title: "Netbeans false downloaded image!"
date: 2007-04-30
forum: Programming Talk
---

### Post by nsleiman on 2007-04-30
I was trying to install netbeans5-5 from the repos, It was recommended (asked actually) to download netbeans-5-5.tar.gz from:
```
http://www.netbeans.info/downloads/all.php?b_id=2323
```
the file size is 82.8MB

I started the download directly to the /tmp/ and i was surprised that the downloaded size was:
```
-rw-r--r-- 1 nohad nohad 181319680 2007-04-30 17:50 netbeans-5_5.tar.gz

```

181MB ?

so the install failed (which is normally the expected result)

i re-downloaded the file but this time to my Desktop and the size was this time correct!

i was wondering if this strange behavior is due to downloading this tarball to the /tmp, konqueror's fault or is it something that can happen from time to another ?

strange no ?:confused:

---

### Post by garlik42 on 2007-04-30
Strange, it sounds like somehow the file was unpacked while being downloaded ...

---

### Post by nsleiman on 2007-04-30
yeah, double size maybe ?

---

### Post by garlik42 on 2007-04-30
I've had internet explorer do that, it takes a tar.gz and uncompresses it and saves an uncompressed tar.tar file.

---

