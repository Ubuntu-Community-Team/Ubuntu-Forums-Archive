---
title: "md5sum - file names with white space"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by icytom on 2013-05-06
Hi,

Im trying to create an md5 hash for a bunch of files ( avoiding the 'avoid' folder)

md5sum $(find . -type f | grep -v '^[.]/avoid/') > md5sums

It seems to do what I want it to do however it breaks when it gets a file name with white space in it.

Ive had a search around and the solution seems to be to add -exec {} + , but I cant figure it out it fits together.

Tom

---

### Post by steeldriver on 2013-05-06
How about

```
find . -path './avoid' -prune -o -type f -exec md5sum {} + > md5sums
```

(the 'path prune' replaces your grep)

---

### Post by icytom on 2013-05-06
yes, that worked perfectly, thank you.

---

### Post by The Trickster on 2013-10-20
I want to use md5sum in Python by using pipe to calculate checksum for a bunch of .mp3 files... is there a command which ignore whitespaces in a input to md5sum program?

---

