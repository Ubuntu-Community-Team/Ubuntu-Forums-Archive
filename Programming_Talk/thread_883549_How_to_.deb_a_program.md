---
title: "How to .deb a program?"
date: 2008-08-08
forum: Programming Talk
---

### Post by StOoZ on 2008-08-08
I've built an open source application , in C++ , used several api's while doing it (wxWidgets , TagLib etc...). it was built in netbeans , how do I pack all the necessery stuff in that .deb file in order to make it run without installing wxwidgets and tablib and all the other libs separately?

---

### Post by loboc on 2008-08-08
use checkinstall instead of make for a quick and dirty package for local use

follow debian guidelines for developers for distribution ready [www.debian.org/doc/debian-policy](www.debian.org/doc/debian-policy)

---

### Post by agapito on 2008-08-08
I guess this would be a good place to start:
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

Have fun :)

---

### Post by loboc on 2008-08-08
> **StOoZ said:**
> I've built an open source application , in C++ , used several api's while doing it (wxWidgets , TagLib etc...). it was built in netbeans , how do I pack all the necessery stuff in that .deb file in order to make it run without installing wxwidgets and tablib and all the other libs separately?

For inclusion of dependencies see this

[http://www.debian.org/doc/debian-policy/ch-binary.html#s3.5](http://www.debian.org/doc/debian-policy/ch-binary.html#s3.5)

and this has a good explanation of whats going on

[http://www.linux.com/articles/60383](http://www.linux.com/articles/60383)

---

### Post by StOoZ on 2008-08-08
ok , seems like according to your links , debian pkg is not what I want now , I would like it to be used on any linux machine.
so I just distribute the source code , and tell the user which dependencies he needs to d/w in order for it to work.
anyhow its a good info - will back it up in my favs.
thanks!!!

so I have some new questions :
in my program , all the libs where installed in the default locations , I have some includes and linking from /use/local/lib ...
how do I know that the user will do the same , if the libs will be installed in a different location , it means that the program will not work right?

---

### Post by loboc on 2008-08-08
I would roll a debian package anyway 
and then put the source in a tar.gz and let the user who has to compile it worry about linking the libraries.  Its not that hard to include a README file listing the source libraries required

---

### Post by Diabolis on 2008-08-08
Read the MOTU wiki: [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

Masters Of The Universe, you'll find all the info there. You'll also find how your .deb can make it into the official repositories.

---

