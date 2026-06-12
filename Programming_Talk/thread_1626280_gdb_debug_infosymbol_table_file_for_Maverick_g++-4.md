---
title: "gdb debug info/symbol table file for Maverick g++-4.5?"
date: 2010-11-20
forum: Programming Talk
---

### Post by gniemcew on 2010-11-20
Hi Everyone,

PROBLEM:

Ubuntu 10.10 (Maverick): I am trying to develop a g++ 4.5 internal plugin, analyzing Abstract Syntax Trees, in the shared library (.so) format and debug it under Code::Blocks. However, Code::Blocks does not seem to be able to breakpoint inside a plugin.so, since (?) g++-4.5 is stripped off of debugging information:

[I]Debugger name and version: GNU gdb (GDB) 7.2-ubuntu
"No symbol table is loaded.  Use the "file" command."[/I]

Some sources mention that **objcopy --add-gnu-debuglink** could be used (?) to associate a debugging information file with a g++-4.5 executable and allow gdb to breakpoint appropriately.

QUESTION:

How does one obtain a debugging information/symbol table file for Maverick g++-4.5 package? I'm not really crazy about compiling and maintaining my own (debug) g++.

G.

---

