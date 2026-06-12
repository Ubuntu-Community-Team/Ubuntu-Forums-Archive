---
title: "how to use a debug package?"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by gxustudent on 2011-10-06
Hi!I would like to ask if I install this dbg package, how can I use it?
I download zlib1g-dbg package:
"sudo apt-get install zlib1g-dbg" in order to debug zpipe program.
I just link the zpipe program with:
“gcc -g zpipe.c -L/usr/lib/debug/lib -lz -Wl,-rpath=/usr/lib/debug/lib/libz.so.1.2.3.3 -o zpipe”,but when the zpipe is linked up, I used “ldd zpipe” find out ,the zpipe still use the default libz in  /lib/,but not the debug shardedlibrary.
And in runtime,I use gdb (info  shared) find out it also use the default version libz.so in /lib !
what thing I can do to use this debug version shared library?

ps :I have try to download zlib source core to make a libzdbg.so.1.2.5 with debug option, but no matter what option I use ,the linker just link the default libz.so in /lib,what thing I can do?

---

