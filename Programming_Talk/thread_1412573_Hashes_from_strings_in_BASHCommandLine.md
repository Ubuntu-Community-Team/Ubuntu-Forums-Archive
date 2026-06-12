---
title: "Hashes from strings in BASH/CommandLine"
date: 2010-02-21
forum: Programming Talk
---

### Post by WaterWalker on 2010-02-21
How can i get a hash from a string using the command line/BASH
I know how to get it from a file($md5sum somefile).
But how do I something like:
$md5sum "123456"
e10adc3949ba59abbe56e057f20f883e

I've tried a lot, but there does not seem to be a way to use strings instead of files.

---

### Post by Barrucadu on 2010-02-21
```
echo -n "a string" | md5sum
```

---

