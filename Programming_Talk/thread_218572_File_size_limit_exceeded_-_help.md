---
title: "File size limit exceeded - help"
date: 2006-07-18
forum: Programming Talk
---

### Post by McScruff on 2006-07-18
hi i built a small programe in c to create a text file.  this file will be huge but when it hits 2gb i get that error, i'm running dapper with ext3 filesystem.

here is my code (sorry for the no tabbing but it was ment to be a quick dirty app and i suck at codeing)

[http://paste.ubuntu-nl.org/18315](http://paste.ubuntu-nl.org/18315)

---

### Post by simonn on 2006-07-18
You have hit the limits for the standard C file functions on a 32 bit system. You need to use functions like fopen64 if you want to greater files sizes.

See:
[http://en.wikipedia.org/wiki/Large_file_support](http://en.wikipedia.org/wiki/Large_file_support)
[http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)

---

