---
title: "C/C++ question"
date: 2005-09-13
forum: Programming Talk
---

### Post by kook44 on 2005-09-13
Hi-
Anyone up for a C/C++ compiling/packaging/linking 101?
Coming from the web application world - Java, PHP, etc. I've always wondered about the "linking" part of C and C++.  Im used to java - import everything you need, compile, and you have an app.
I never really got the whole linking thing - kinda breezed thru that in my undergrad classes.

---

### Post by cwaldbieser on 2005-09-13
[QUOTE=kook44]Hi-
Anyone up for a C/C++ compiling/packaging/linking 101?
Coming from the web application world - Java, PHP, etc. I've always wondered about the "linking" part of C and C++.  Im used to java - import everything you need, compile, and you have an app.
I never really got the whole linking thing - kinda breezed thru that in my undergrad classes.[/QUOTE]
When you compile, you just create the .o files.  Because you normally don't write all the code that runs yourself, the .o files will contain some symbols that represent the entry points for external functions, etc. that are located in an external library.  The linker's job is to resolve these "place holders".  During static linking, the external code is just copied in.  For dynamic linking, the linker writes the code to load the dynamic library.  The linker also can recalculate the actual addresses that instructions are located at and branch to.

---

