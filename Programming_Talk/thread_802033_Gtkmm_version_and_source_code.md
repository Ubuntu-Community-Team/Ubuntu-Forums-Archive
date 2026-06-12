---
title: "Gtkmm version and source code"
date: 2008-05-21
forum: Programming Talk
---

### Post by xlinuks on 2008-05-21
Hi,
1) Please let me know someone how to check the Gtkmm version (from C++), in Java I do so by using System.getProperty( "java.version" );

2) I'm using NetBeans 6.1 for Gtkmm learning/programming and I installed the libgtkmm-2.4-dev and libgtkmm-2.4-doc packages from the command line.
NetBeans works fine with that - it found the compiler and the documentation (the .h files).
How do I also install the source code (from the command line as well, there seems to be no libgtkmm-2.4-src, perhaps it's called otherwise)? - for I it also has the feature to point to/open the source code of a given (gtkmmm) file.

Thanks for your time.

---

### Post by JupiterV2 on 2008-05-21
> **xlinuks said:**
> Hi,
1) Please let me know someone how to check the Gtkmm version (from C++), in Java I do so by using System.getProperty( "java.version" );

I'm not sure if this is exactly what you're looking for but I'm assuming you're wanting to check this during installation since I can't see why you would to while the program is running. Using autoconf, you can enter this line into your autoconf.ac file. It will also define GTKMM_CFLAGS and GTKMM_LIBS for you.

```
PKG_CHECK_MODULES(GTKMM, gtkmm-2.4 >= 2.12.0)
```

There is probably a way to put this in a regular Makefile or within a bash script too, perhaps by parsing the output from pkg-config:

```
pkg-config gtkmm-2.4 --modversion
```

> 
2) I'm using NetBeans 6.1 for Gtkmm learning/programming and I installed the libgtkmm-2.4-dev and libgtkmm-2.4-doc packages from the command line.
NetBeans works fine with that - it found the compiler and the documentation (the .h files).
How do I also install the source code (from the command line as well, there seems to be no libgtkmm-2.4-src, perhaps it's called otherwise)? - for I it also has the feature to point to/open the source code of a given (gtkmmm) file.

I know the development source package is called libgtkmm-2.4-dev. Generally, in Ubuntu, the sources have -dev as their post-fix, not -src.

```
sudo apt-get install libgtkmm-2.4-dev
```

This may not be 100% right. I don't usually install from the command line...

> Thanks for your time.
You're welcome. =)

---

