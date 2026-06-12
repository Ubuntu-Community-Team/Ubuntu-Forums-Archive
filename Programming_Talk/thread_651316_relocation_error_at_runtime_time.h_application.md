---
title: "relocation error at runtime time.h application"
date: 2007-12-27
forum: Programming Talk
---

### Post by morngrar on 2007-12-27
I'm making an app for a friend that will print out an html file from a database. This html file will also show when it was last updated.(the exact time when the html-printing function is called) I've used time.h and it compiles, but at runtime, when the html-printing function is called, the program crashes with this error: "relocation error: /usr/lib/libstdc++.so.6: symbol read, version GLIBC_2.0 not defined in file libc.so.6 with link time reference"

I've googled enough, but couldn't find an understandable answer.

I've used g++ 4.1.2 to compile the app (which is the latest version in the ubuntu repo at the point of writing)

this is rly getting on my nerves....


EDIT
i managed a workaround... somehow xD

---

