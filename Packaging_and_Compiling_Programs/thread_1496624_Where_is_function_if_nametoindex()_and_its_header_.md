---
title: "Where is function if_nametoindex() and its header file if.h ?"
date: 2010-05-29
forum: Packaging and Compiling Programs
---

### Post by Kerubu on 2010-05-29
Hi,

I'm trying to learn some network programming and I was poking around on the GNU website and the documentation for libc. In particular I was interested in the functions for network devices, as described here :

[http://www.gnu.org/software/libc/manual/html_node/Interface-Naming.html#Interface-Naming]("http://www.gnu.org/software/libc/manual/html_node/Interface-Naming.html#Interface-Naming")

There are several useful functions here that I want to use but when on my Ubuntu 10.04 installation, the header file does not exist in the right location and it doesn't contain any of the function decelerations. 

GNU states to include <net/if.h> but on my installation it's under <linux/if.h> and doesn't have the function decelerations.

Where has Ubuntu put them or are these obsolete functions ?

Many thanks

Kerubu

---

### Post by MadCow108 on 2010-05-29
its in the package libc6-dev and gets placed in /usr/include/net
it should be installed on your system if you have build-essential installed

---

### Post by Kerubu on 2010-05-30
> **MadCow108 said:**
> its in the package libc6-dev and gets placed in /usr/include/net
it should be installed on your system if you have build-essential installed

Thanks MadCow108.

I did have it all the time, it was an error in my code that prevented it from being compiled !

---

### Post by u1106 on 2010-05-31
Good you solved it already. However, such questions come up frequently when coding, so I'll give a general answer.

For searching installed files the command is

```
find / -name *filename* 2>/dev/null

```in case of header files it should be pretty safe to start searching from /usr/include instead of /


For files not yet installed you can use apt-file. (This command is the contained in the package with the same name, it's not not installed by default)

---

