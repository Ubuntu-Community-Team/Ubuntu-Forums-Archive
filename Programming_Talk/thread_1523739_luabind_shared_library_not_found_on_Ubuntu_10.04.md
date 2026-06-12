---
title: "luabind shared library not found on Ubuntu 10.04"
date: 2010-07-04
forum: Programming Talk
---

### Post by MattThLinuxNewb on 2010-07-04
Hey guys,
I'm writing a small C++ app with LUA scripting using the luabind library and I've just started porting it to Ubuntu Lucid (I've previously been developing on Hardy where it compiles and runs with no problems). Changing the project to work with Lua 5.1 went OK, and it compiles all right but now I get this when I run it:
```
./missile: error while loading shared libraries: libluabind.so.0: cannot open shared object file: No such file or directory
```
The libluabind-dev and libluabind0.9.0 packages are installed, which includes /usr/lib/libluabind.so.0.9.0
How do I get it to use libluabind.so.0.9.0 rather than libluabind.so.0?

Thanks in advance,
Matt

---

