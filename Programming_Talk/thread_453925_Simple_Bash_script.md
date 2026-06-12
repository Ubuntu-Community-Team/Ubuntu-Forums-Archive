---
title: "Simple Bash script"
date: 2007-05-24
forum: Programming Talk
---

### Post by kilroy423 on 2007-05-24
I'm trying to find ips out of logs by using grep and having a hard time doing so...what do I have wrong?


#! /bin/bash

grep [0-255].[0-255].[0-255].[0-255] /.../.../  >/.../.../...


thx,
dan

---

### Post by ghostdog74 on 2007-05-24
can you show a sample of the logs..

---

### Post by lloyd_b on 2007-05-24
Try this one (Note: use "egrep" or "grep -E")
```
egrep  "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}"
```"

The "[...]" ranges are for searching for SINGLE CHARACTERS.  So "[0-9]" looks for the digits 0 through 9.  I have no clue what [0-255] would match :-)

The "{1,3}" tells it to match the preceding expression a minimum of 1 time, and a maximum of 3 times.  So "[0-9]{1,3}" searches for a 1 to 3 character sequence, with each of the characters in the range 0 through 9.

Note the "\." rather than a simple "." - in grep, "." matches ANY character.  The preceding backslash "escapes" it so that grep will search for a literal period.

Final Note: there's a "[:digit:]" construct that should be equivalent to "[0-9]", but I'd rather type the latter (it's shorter, if nothing else).

Lloyd B.

---

### Post by kilroy423 on 2007-05-24
Well, the [0-255] is to include all possible ip addresses since a ip can be any number 1-255..an exampe of a log would be /var/log/auth.log which if you were getting attacked or had multiple connections would be full of ips.  By using this script it would be easy to go through the outputted ips and decide who is supposed to be there and who isn't by looking at a relatively small number of ips rather then a whole log full of text lines.

thx and i will try egrep and get back to you guys

dan

---

### Post by kilroy423 on 2007-05-25
Ok, thx that worked just fine...now I understand to use 1-9 and not 0-255...thx alot



dan

---

