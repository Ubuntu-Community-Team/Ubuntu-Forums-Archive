---
title: "Compiling C++ programs"
date: 2007-01-08
forum: Programming Talk
---

### Post by fbelange on 2007-01-08
Hi,

I've just installed Ubuntu 6.10 and can't get my C++ programs to compile.  When I attempt to compile them, I get the following error:

gcc: error trying to exec 'cc1plus': execvp: No such file or directory

Anyone have any idea what it means?

Thanks,
Francois

---

### Post by xtacocorex on 2007-01-08
Have you installed the build-essential package that has the most used development tools?
```
sudo apt-get install build-essential
```
That could be one reason why it isn't working.

---

### Post by olejorgen on 2007-01-08
Hm.. try g++ instead

---

### Post by fbelange on 2007-01-08
G++ was my first point of call, but for some reason it didn't work.

But once I got the packages you described, I had G++ and everything compiled fine.

Thanks for the help!

Francois

P.S. I'm surprised that the "build-essential" packages don't come with the default installation.

---

