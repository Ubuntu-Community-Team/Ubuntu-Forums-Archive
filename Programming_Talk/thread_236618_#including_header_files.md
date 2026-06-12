---
title: "#including header files"
date: 2006-08-15
forum: Programming Talk
---

### Post by SolarBear on 2006-08-15
Hi !

I need to use the [C++ Sockets library]("http://www.alhem.net/Sockets/download.html") and try the examples given. However, obviously, I can't use a simple

```
#include <TcpSocket.h>
```since it's not a "standard" library.

Now, I don't much about gcc. What I'd like to know is
1) how can I package the library to a .deb and install it
or
2) place them in some directory and link to it

The first solution would be best, I guess. Anyway, any help would be appreciated.

Thanks !

---

### Post by simonn on 2006-08-15
Probably not what you want to do.

I have had a quick look at the Makefile in the tar.gz and it seems as if all you will need to do is to extract the tarball to somewhere, cd into it's dir and make && make install.

This will install it with the prefix /usr/local.

This means that header files will be in /usr/local/include/Sockets and libs in /usr/local/lib (see [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html) for more info on the linux filesystem hierarchy).

This should now be visible to the compiler, by default gcc should look in /usr/local/include and link to libraries in /usr/local/lib.

To include any of the Sockets library's header files use:

#include <Sockets/[headerfile]>

---

