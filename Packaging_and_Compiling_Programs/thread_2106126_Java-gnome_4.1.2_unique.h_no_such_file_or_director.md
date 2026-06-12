---
title: "Java-gnome 4.1.2 unique.h no such file or directory"
date: 2013-01-18
forum: Packaging and Compiling Programs
---

### Post by db579 on 2013-01-18
I'm trying to compile java-gnome 4.1.2 from source ([http://ftp.gnome.org/pub/gnome/sources/java-gnome/4.1/](http://ftp.gnome.org/pub/gnome/sources/java-gnome/4.1/)) following the instructions given here: [http://java-gnome.sourceforge.net/README.html](http://java-gnome.sourceforge.net/README.html) 

I'm using 64 bit Ubuntu 12.04

./ configure works fine and suggests all the dependencies are met but when I use make I get the following error message:

```

MKDIR	tmp/objects/org/gnome/unique
GCC	generated/bindings/org/gnome/unique/UniqueApp.c
generated/bindings/org/gnome/unique/UniqueApp.c:44:27: fatal error: unique/unique.h: No such file or directory
compilation terminated.
make: *** [build-java] Error 1

```

Can anyone help? Thanks

---

