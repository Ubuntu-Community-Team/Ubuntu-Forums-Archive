---
title: "No /usr/lib/libmd5.so in 10.04 LTS"
date: 2010-07-22
forum: Packaging and Compiling Programs
---

### Post by babzog on 2010-07-22
Hey folks,

I have an app (C code) that I'm trying to compile on 10.04 that is trying to link against libmd5.  I cannot find this lib nor can I find the package that should supply it.  Tried libssl-devel, libdigest-md5-perl, libcrypt-devel, all to no avail (none supply that lib).

Can you please point me to the correct package (or to the package that would replace it - the code is admittedly old) or where I can obtain the source for libmd5?

Thanks!

---

### Post by anglican on 2010-07-26
> **babzog said:**
> Hey folks,

I have an app (C code) that I'm trying to compile on 10.04 that is trying to link against libmd5.  I cannot find this lib nor can I find the package that should supply it.  Tried libssl-devel, libdigest-md5-perl, libcrypt-devel, all to no avail (none supply that lib).

Can you please point me to the correct package (or to the package that would replace it - the code is admittedly old) or where I can obtain the source for libmd5?

Thanks!
It may be that the necessary functions are in the libbsd-dev package, so you could try compiling with -lbsd instead of -lmd5.

H

---

