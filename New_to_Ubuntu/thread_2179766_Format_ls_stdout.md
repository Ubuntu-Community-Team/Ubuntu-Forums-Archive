---
title: "Format ls stdout"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by geohei on 2013-10-09
Hi.

I'd like to create a list of all files in a filesystem in order to pipe it to md5sum. First I need a list of all files. Every line a new file.

When I say ...
```
root@io:/media/data_raid0/# transfer# ls -R
.:
1  2

./1:
a

./2:
b
```
... I get lots of lines which are != files.

Which options should I use with ls in order to get this?
```
root@io:/media/data_raid0/# transfer# ls -?
1/a
2/b

```
Thanks,

---

### Post by steeldriver on 2013-10-09
You should probably use 'find' instead of 'ls -R'

```
find /path/to/filesystem/root -type f
```

EDIT: you could even skip the pipe and just do

```
find /path/to/filesystem/root -type f -exec md5sum {} \;
```

---

### Post by geohei on 2013-10-10
This works perfect.
Thanks a lot!

---

