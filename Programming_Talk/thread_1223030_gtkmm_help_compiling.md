---
title: "gtkmm help compiling"
date: 2009-07-25
forum: Programming Talk
---

### Post by DGortze380 on 2009-07-25
Hey All,

Trying to teach myself gtkmm, but having trouble getting the tutorial to compile ...

I've installed libgtkmm-dev.

Following the tutorial I've got a source file I'm trying to compile with:
 
g++ hello.cpp -o hello `pkg-config gtkmm-2.4 --cflags --libs`

Returns the errors:

Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found
hello.cpp:1:19: error: gtkmm.h: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:5: error: ‘Gtk’ has not been declared
hello.cpp:5: error: expected `;' before ‘kit’
hello.cpp:7: error: ‘Gtk’ has not been declared
hello.cpp:7: error: expected `;' before ‘window’
hello.cpp:9: error: ‘Gtk’ has not been declared
hello.cpp:9: error: ‘window’ was not declared in this scope

---

### Post by MadCow108 on 2009-07-25
pkg-config does not find the gtkmm-2.4 file
are you sure you have libgtkmm-2.4-dev installed?
libgtkmm-dev are the gtk+1.2 dev files

---

### Post by DGortze380 on 2009-07-25
> **MadCow108 said:**
> pkg-config does not find the gtkmm-2.4 file
are you sure you have libgtkmm-2.4-dev installed?
libgtkmm-dev are the gtk+1.2 dev files

#-o

problem solved...

---

