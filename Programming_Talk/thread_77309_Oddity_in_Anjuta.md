---
title: "Oddity in Anjuta"
date: 2005-10-16
forum: Programming Talk
---

### Post by terminalspin on 2005-10-16
I have been looking at Anjuta in Ubuntu 5.10 for C++ development on gtkmm. 

I'm not an experienced C++ programmer - I come from a Java background, so I may well have missed something, but...

My program compiles OK, but If I use the built in Build | Build command, I get the following output:- 

[INDENT][FONT="Courier New"]Building file: testgtkmm.cc ...
g++  `pkg-config --cflags gtkmm-2.4`      "testgtkmm.cc"   `pkg-config --libs gtkmm-2.4`    -o "testgtkmm"
g++: `pkg-config: No such file or directory
g++: gtkmm-2.4`: No such file or directory
g++: `pkg-config: No such file or directory
g++: gtkmm-2.4`: No such file or directory
cc1plus: error: unrecognized command line option "-fcflags"
cc1plus: error: unrecognized command line option "-flibs"
Completed ... unsuccessful
Total time taken: 0 secs[/FONT][/INDENT]

However, if I enter the same g++ command in a terminal, it compiles and links fine.
[INDENT][FONT="Courier New"]g++  `pkg-config --cflags gtkmm-2.4`      "testgtkmm.cc"   `pkg-config --libs gtkmm-2.4`    -o "testgtkmm"[/FONT][/INDENT]

My build command under Settings | Commands is the default [FONT="Courier New"]g++ $(anjuta.compiler.flags) "$(current.file.name.ext)" $(anjuta.linker.flags) -o "$(current.file.name)"[/FONT]

Does anyone have any ideas?

thanks,

T

---

### Post by wmcbrine on 2005-10-17
It looks like it's not going through the shell, so the backticks aren't being interpreted. I dunno why, though. It's as though it were using exec() when it should be using system(), or something.

---

