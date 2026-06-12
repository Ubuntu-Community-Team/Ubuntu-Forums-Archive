---
title: "/usr/bin/ld: cannot find -llibmysqlclient.a"
date: 2007-05-15
forum: Programming Talk
---

### Post by jacket87 on 2007-05-15
Hello,
    I'm getting this message when I try to compile/link an application in Eclipse:
/usr/bin/ld: cannot find -llibmysqlclient.a

I'm running Ubuntu 7.04 - Fiesty Fawn
Eclipse version 3.2.2
Synaptic Package Manager indicates that libmysqlclient15-dev is installed.

I  have tried explicitly putting the path to libmysqlclient.a, but still get the same error.

Now I'm pulling out what is left of my hair.  Any suggestions?

Thanks.

---

### Post by WW on 2007-05-15
With the -l option, you do not include the "lib" part of the library name.  Try **-lmysqlclient**

---

### Post by jacket87 on 2007-05-16
That got it.  Thank you very much.

---

