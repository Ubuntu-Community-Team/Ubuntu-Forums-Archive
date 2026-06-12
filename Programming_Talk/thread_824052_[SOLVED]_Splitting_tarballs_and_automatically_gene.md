---
title: "[SOLVED] Splitting tarballs and automatically generated md5 checksums"
date: 2008-06-09
forum: Programming Talk
---

### Post by altonbr on 2008-06-09
I'll be needing to create a very large (10GB) tarball and I will need to split it into 10 pieces. I will then need to md5sum all of the 10 pieces before and after the transfer.

Is there a script that someone has that can just do this?

I've done my fair share of BASH scripting, including setting up automatic rsyncing over SSH, but I've never really worked with tar, gzip and md5sum.

---

### Post by Phenax on 2008-06-09
Hello, tar and gunzip do not natively support making a multi-part file. The "rar" utility supports this..

But you can use the 'Split' utility to split your file. It is simple to use.
```
split -b 1G
```
would split your file into however-many one gigabyte files needed. The manual page explains more about the Split utility.

The md5sum utility is similarly easy.
```
md5sum filename
```
Again - use the man-page for more advance option..

To assemble the files again, just join them together. The easiest way I know would be to write a loop to do such:
```
cat file2 >> file1 && rm file2
```
```
cat file3 >> file1 && rm file3
```
And on.. obviously using a loop or globbing technique to do

---

### Post by altonbr on 2008-06-09
That's amazing, thank you!

Forgot Linux/Unix is all about little utilities doing one thing and one thing well!

---

