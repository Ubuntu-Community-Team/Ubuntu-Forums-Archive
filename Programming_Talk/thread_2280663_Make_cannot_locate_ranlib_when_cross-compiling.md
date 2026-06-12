---
title: "Make cannot locate ranlib when cross-compiling"
date: 2015-06-01
forum: Programming Talk
---

### Post by kerry3 on 2015-06-01
Hello all,

I am trying to cross-compile openssl for use on a Raspberry Pi.  The building process goes OK, but when I attempt to install, I get an error telling my that it cannot find the x-tools ranlib.  Here's what I'm trying:

```

$ git clone git://git.openssl.org/openssl.git
$ cd openssl
$ ./Configure linux-armv4 no-ssl2 no-ssl3 no-comp --cross-compile-prefix=arm-unknown-linux-gnueabi- --openssldir=/opt/rpi/openssl
$ make depend
$ make
$ sudo make install -> breaks here!
```

The last bit of output from "sudo make install" is:
```

installing libcrypto.a
/bin/sh: 6: arm-unknown-linux-gnueabi-ranlib: not found
make: *** [install_sw] Error 127
```

I'm sure my path is correct because from the same directory (or any other directory) I can do this (and also because the "make" step worked without complaints):
```

$ arm-unknown-linux-gnueabi-ranlib -v
GNU ranlib (crosstool-NG 1.21.0) 2.25
Copyright (C) 2014 Free Software Foundation, Inc.
This program is free software; you may redistribute it under the terms of
the GNU General Public License version 3 or (at your option) any later version.
This program has absolutely no warranty.
```

Any ideas?  I'm running Ubuntu 14.04 x64.  Any help is appreciated!

Thanks,

Kerry

EDIT:  Removed some extra info, which further research suggests has no bearing on my issue...

---

### Post by kerry3 on 2015-06-02
Wow.  After several hours of banging my head against a wall, I realized that sudo was resetting my path.  So make really couldn't find the arm-unknown-linux-gnueabi-ranlib.

The solution was to use
```
$ sudo su -p
# make install
# exit
```

instead of 

```
$ sudo make install
```

Thanks,

Kerry

---

