---
title: "checking for C compiler default output file name"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Hirashgeff on 2008-06-01
every time i try to run   "configure" file in any source package
following error comes
"checking for C compiler default output file name"
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

I'm using KUBUNTU 8.04
Help me to solve this

---

### Post by sdennie on 2008-06-01
Have you done the following:

```

sudo apt-get install build-essential

```

---

