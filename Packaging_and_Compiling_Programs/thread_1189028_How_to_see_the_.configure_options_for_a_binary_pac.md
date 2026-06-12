---
title: "How to see the ./configure options for a binary package?"
date: 2009-06-16
forum: Packaging and Compiling Programs
---

### Post by nutznboltz on 2009-06-16
In order to know what features are enabled for certain packages one must know what ./configure options were used at compile time.

Given a binary package, how does one tell what ./configure options were used at compile time? Are they listed in a file or on a web page anywhere?

I searched for this a number of ways but could not find anything about it.

Thanks

---

### Post by nutznboltz on 2009-07-15
Seems you have to poke through the "debian/rules" file and see what the package does.  There does not appear to be a standard approach.

---

### Post by laney on 2009-07-16
> **nutznboltz said:**
> In order to know what features are enabled for certain packages one must know what ./configure options were used at compile time.

Given a binary package, how does one tell what ./configure options were used at compile time? Are they listed in a file or on a web page anywhere?

I searched for this a number of ways but could not find anything about it.

Thanks

You cannot see this from a binary package. What you want to do is download the *source* package using `apt-get source package' and then have a look at debian/rules as was mentioned above. It might not look like ./configure --args, but could be in a variable such as DEB_CONFIGURE_EXTRA_ARGS or in a call to dh_auto_configure.

---

