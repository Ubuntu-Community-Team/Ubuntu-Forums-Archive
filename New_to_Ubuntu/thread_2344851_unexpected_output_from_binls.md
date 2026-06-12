---
title: "unexpected output from /bin/ls"
date: 2016-11-28
forum: New to Ubuntu
---

### Post by hannaybuchan on 2016-11-28
Given a directory containing files
 ```
 Jethro
  simon
  .doofus
  glamour
  Foggy
  ..foo
  17try
```
In flavors of UNIX I have used - from v6 through BSD to the unixy Mac OS X - the result of /bin/ls -Al is "ASCII-ordered":
  ```
..foo
  .doofus
  17try
  Foggy
  Jethro
  glamour
  simon
```
But in a fresh install of 16.04, /bin/ls -Al ignores the "dots" and ignores case and produces
 ```
 17xray
  .doofus
  Foggy
  ..foo
  glamour
  Jethro
  simon
```
Also, /usr/bin/sort on a list of the filenames behaves the same way. Is there a way to get the "classic" output instead?

---

### Post by kpatz on 2016-11-28
Run this command:```
export LC_ALL=POSIX
``` and then both ls and sort will sort the way you want.

Add that same line to your ~/.bashrc file to make it permanent.

---

### Post by hannaybuchan on 2016-11-28
Thanks!

---

### Post by sisco311 on 2016-11-28
Welcome to the forums, hannaybuchan!

LC_ALL is meant to be used only for testing and troubleshooting.  

Please check out:  [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

The LC_COLLATE variable governs the collation rules; Setting it to `C' or `POSIX' will give you the desired behaviour.

---

