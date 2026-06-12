---
title: "compile ajunta: No package gdl-3.0 found"
date: 2012-01-08
forum: Packaging and Compiling Programs
---

### Post by master.t on 2012-01-08
Hey,

I am trying to compile anjuta on Ubuntu 11.10. I have tried both compiling "apt-get source" as compiling the 3.2.2 from the anjuta website.

The ./configure fails with:

```
configure: error: Package requirements (gdl-3.0 >= 2.91.4) were not met:
No package gdl-3.0 found.
```

"dpkg -l | grep gdl" on my system returns:
```
rc  libgdl-1-3                             2.30.1-1
              GNOME DevTool libraries
ii  libgdl-3-1                             3.1.5-0ubuntu1
              GNOME DevTool libraries
ii  libgdl-3-common                        3.1.5-0ubuntu1
              GNOME DevTool libraries - common file
```

How can I solve this?

Thanks,
Wkr,

Tom

---

### Post by MadCow108 on 2012-01-09
you need to install libgdl-3-dev

to get everything you need you can use apt-get build-dep anjuta
or mk-build-deps -i -r from the devscripts package executed in the anjute package source tree

---

