---
title: "where are files installed by libsoci-sqlite3-gcc?"
date: 2010-12-15
forum: Programming Talk
---

### Post by stuque on 2010-12-15
I am trying to get the SOCI database interface working with Sqlite3 on Ubuntu. I've installed the libsoci-sqlite3-gcc and libsoci-core-gcc packages with synaptic, but I can't find where on my system and SOCI files or folders have been installed. 

So can anyone tell me where I can find the SOCI folders and files?

---

### Post by zobayer1 on 2010-12-16
> **stuque said:**
> I am trying to get the SOCI database interface working with Sqlite3 on Ubuntu. I've installed the libsoci-sqlite3-gcc and libsoci-core-gcc packages with synaptic, but I can't find where on my system and SOCI files or folders have been installed. 

So can anyone tell me where I can find the SOCI folders and files?

You can use the whereis command.
[http://ss64.com/bash/whereis.html](http://ss64.com/bash/whereis.html)

---

### Post by MadCow108 on 2010-12-16
the soci libraries get placed in /usr/lib
they have a rather weird naming:
libsoci_core-gcc-3_0.so and libsoci_sqlite3-gcc-3_0.so
the dev package installs the headers in /usr/include/soci

you have to pass -I/usr/include/soci -lsoci_core-gcc-3_0 -lsoci_sqlite3-gcc-3_0 to the compiler to compile code using it

note that soci has been removed from debian squeeze and so it could get removed from ubuntu natty too, I plan to package it again when they finally release 3.1
In that case the weird naming will also change

---

### Post by gmargo on 2010-12-16
> **stuque said:**
> I've installed the libsoci-sqlite3-gcc and libsoci-core-gcc packages with synaptic, but I can't find where on my system and SOCI files or folders have been installed.

Use the **dpkg** tool with the **-L** (or --listfiles) option.
```

dpkg -L libsoci-sqlite3-gcc
dpkg -L libsoci-core-gcc

```

However, if you're compiling, you'll also need to install the libsoci-core-gcc-dev package.

---

### Post by stuque on 2010-12-16
The problem was that I forgot to install the -dev headers package. Doh! Thanks for the replies.

---

