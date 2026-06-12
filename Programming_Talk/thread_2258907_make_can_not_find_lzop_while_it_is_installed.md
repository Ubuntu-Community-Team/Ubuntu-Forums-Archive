---
title: "make can not find lzop while it is installed"
date: 2014-12-31
forum: Programming Talk
---

### Post by shahin on 2014-12-31
I am doing some cross compiling using make, and I get the following error: 

```
/bin/sh: 1: lzop: not found
```

I can issue lzop command, and get the output so I am not sure why make has an issue with it. Any help is greatly appreciated.

I found out what I was doing wrong. Can I delete this question somehow? #-o

---

### Post by schragge on 2014-12-31
Well that means *lzop* is not on PATH when make tries to call it. Find out the full path name of lzop:
```
which lzop
```
Then look up the PATH value that make uses:
```
make -p 2>/dev/null|grep ^PATH
``` and ensure that directory where lzop binary is located is included.

---

### Post by shahin on 2014-12-31
@ Schrage - Thanks

---

