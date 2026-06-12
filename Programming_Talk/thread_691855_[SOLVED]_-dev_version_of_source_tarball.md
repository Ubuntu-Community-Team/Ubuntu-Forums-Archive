---
title: "[SOLVED] -dev version of source tarball?"
date: 2008-02-09
forum: Programming Talk
---

### Post by kripkenstein on 2008-02-09
Maybe this is a trivial question.

I know that to compile my own programs with some library, I need to install the -dev package for that library. That brings in the .h files into the appropriate /include directory, and so forth.

Now, say I get the library in tarball form, which I just did for [gobject-introspection]("http://svn.gnome.org/viewvc/gobject-introspection/trunk/") (seems interesting, thought I'd check it out). make and make install installs just the binary .so files, etc., it doesn't install the .h files anywhere. So I have in a sense the binary part of the library, but not the -dev part.

How do I get the -dev part of it? Is there some standard way during the make/make install process in which I can tell a package to install its .h files into /include? (I can see the .h files inside gobject-introspection, they just don't get installed anywhere) Or are there separate tarballs for the -dev versions?

---

### Post by Compyx on 2008-02-09
Normally when installing a library from source, the headers do get installed. Try looking in /usr/local/include. You can specify the prefix in which a library or applications gets installed by passing --prefix=.... to ./configure. Many sources using autotools have a default prefix of /usr/local when installing.

You can also check what gets installed where by passing -n to make, ie:
```

make -n install

```
will pretend to `make install` but only outputs the commands it would normally execute.

---

### Post by kripkenstein on 2008-02-09
> **Compyx said:**
> Normally when installing a library from source, the headers do get installed. Try looking in /usr/local/include. You can specify the prefix in which a library or applications gets installed by passing --prefix=.... to ./configure. Many sources using autotools have a default prefix of /usr/local when installing.

You can also check what gets installed where by passing -n to make, ie:
```

make -n install

```
will pretend to `make install` but only outputs the commands it would normally execute.
Thanks, after reading what you wrote, I managed to figure it out. I had the change the prefix and a few other things.

Also "make -n install" is very useful.

---

