---
title: "Debugging gtk"
date: 2009-02-12
forum: Programming Talk
---

### Post by wtruong on 2009-02-12
hi all,

I'm trying to fix a person's gtk app.  Does anyone know how to debug the app with gdb or ddd?

---

### Post by Tony Flury on 2009-02-12
ok - some questions : 

What language is it written in ?
Do you have the source code ?
Have you used gdb or ddd before ?

gdb or ddd are not a magic bullet - they help you find bugs - mainly by stepping through the code, and inspecting variables as they change.

In general  - debugging is often a case of finding out where the code breaks, and placing break points just before the bug, so you can see what the values are just before the bug - it is normally these that give you clues as to why the code is failing.

Without the source code you will have a tough time, and even with the source, the application will need to be built  with the relevant flags/options so that gdb or ddd can associate the programm and the memory locations with the source code and varibale names, and you can make meanigful use of what gdb/ddd are showing you.

---

### Post by jespdj on 2009-02-12
I don't know exactly what you want to do, but I recently read this:

[VMware developers release GUI debugging tool for GTK+](http://arstechnica.com/open-source/news/2009/01/vmware-developers-release-gui-debugging-tool-for-gtk.ars)

Might be useful for debugging your GTK+ application.

---

### Post by wtruong on 2009-02-12
Yes I do know how to use gdb/ddd.  The source code is in c.  I 've never debugged ui apps before but I know how to debug

---

### Post by rich1939 on 2009-02-12
> **wtruong said:**
> Yes I do know how to use gdb/ddd.  The source code is in c.  I 've never debugged ui apps before but I know how to debug

If you use CODE::BLOCKS as your editor, compiler, linker, debugger-interface, debugging is very simple. Just click next to the line(s) where you want breakpoint(s) and start the debugger from the CODE::BLOCKS "Debug" menu. You can add "watch" points, examine local and/or global variables, etc. It's very nice.

---

### Post by wtruong on 2009-02-12
my box only has gdb/ddd and has no connection to the outside world :(

---

### Post by wtruong on 2009-02-12
nvm stupid me, ddd works....... i forgot to add a -g....

---

