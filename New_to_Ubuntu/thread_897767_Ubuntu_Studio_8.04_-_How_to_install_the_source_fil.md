---
title: "Ubuntu Studio 8.04 - How to install the source files ?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Dimark on 2008-08-22
Hi,

I installed Ubuntu Studio 8.04 from DVD.

Now I have to install the driver package for the wireless lan card (RTL8185L) or the at least the ndiswrapper, but he makefiles are missing the sources.

I even have not a directory called "/lib/modules/2.6.24-rt/build"


How the sources can be installed ?

Thanks, Dimark

---

### Post by neurostu on 2008-08-22
Is there a autogen.sh file what about a configure file?

sometimes they can generate the make file...
try:
```

./autogen.sh
or
./configure

```

---

### Post by Dimark on 2008-08-22
when I execute "make" for the ndiswrapper, "can not find kernel version..." is displayed.

./autogen.sh and ./configure do not work.

---

