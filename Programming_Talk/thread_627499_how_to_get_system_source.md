---
title: "how to get system source?"
date: 2007-11-30
forum: Programming Talk
---

### Post by outer_space on 2007-11-30
I can find the system header files, but where are or how do I get the source .c files that go with them?  I am looking at the accept function and want to find out what errno gets set to means.  It does not say this in the header but it would have to say it in the source .c file but I cannot find this file.

Thanks.

---

### Post by Compyx on 2007-12-01
Assuming you're talking about accept(3):

accept(3) is part of GLibc, so you should install the source of glibc:
```

apt-get source glibc

```

After that, cd into the directory 'glibc-2.6.1' and untar the 'glibc-2.6.1.tar.bz2' file.
The accept.c file is in the directory 'socket'.

The above version numbers may be different on your box, but I assume you get the picture.

The error code is ENOSYS, by the way.

---

