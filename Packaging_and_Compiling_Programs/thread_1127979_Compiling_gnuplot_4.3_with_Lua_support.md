---
title: "Compiling gnuplot 4.3 with Lua support"
date: 2009-04-17
forum: Packaging and Compiling Programs
---

### Post by jazzgossen on 2009-04-17
I'm trying to build gnuplot 4.3 with the lua/TikZ terminal. I have installed both the "lua50" and the "lua5.1" packages as well as "liblua5.1-dev" and "liblua50-dev". Still, when I run "configure --with-lua" I get the following output in configure.log

```
configure:11888: checking for LUA
configure:11896: $PKG_CONFIG --exists --print-errors "lua"
Package lua was not found in the pkg-config search path.
Perhaps you should add the directory containing `lua.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lua' found
configure:11899: $? = 1
No package 'lua' found
configure:11945: result: no
configure:11960: WARNING: The lua terminal will not be compiled.

```

Has anyone else compiled gnuplot with lua/TikZ on Ubuntu 8.10?

---

### Post by johnl on 2009-04-17
It looks like the configure script is looking for "lua" in the pkgconfig directory.  The problem is that liblua5.1-0-dev creates a pkgconfig entry called "lua5.1".  

I think the easiest way around this is to create a link from "lua.pc" to "lua5.1.pc" so that pkgconfig recognizes requires for just plain "lua":
```

cd /usr/lib/pkgconfig
sudo ln -s lua5.1.pc lua.pc

```

You can verify that this worked by running:
```

pkg-config --cflags "lua"

```
And making sure that it does not complain about not finding a package.


Hope this helps.

---

### Post by jazzgossen on 2009-04-19
Thanks, that did it!

---

