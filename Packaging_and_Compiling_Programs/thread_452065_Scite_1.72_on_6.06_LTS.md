---
title: "Scite 1.72 on 6.06 LTS"
date: 2007-05-22
forum: Packaging and Compiling Programs
---

### Post by NathanB on 2007-05-22
Per instructions, I go into /scintilla/gtk/ and do a "sudo make" but it stumbles all over the place.  Doing a "make deps" suggests that I should add the directory containing "gtk+-2.0.pc" but when I do a "find -iname gtk+-2.0.pc" from root it can't find that file.

Also, I am not sure if this is related at all, but the Scite README talks about static linking here:
"The current make file only supports static linking between SciTE and Scintilla."

The README.Debian from "/usr/share/doc/libgtk2.0-0" has this to say about it:
"If you wish to link the GTK+ 2.0 libraries statically into your program,
please note that you *can not* use the '-static' flag to gcc.
Instead, you have to link your program *dynamically* and link *only*
the GTK+ 2.0 libraries statically, like this:

$ gcc -export-dynamic -o foo foo.c \
  -Wl,-Bstatic `pkg-config --cflags --libs gtk+-2.0` -Wl,-Bdynamic \
  [other dynamically linked libraries]

The reason for this is that GTK+ 2.0 uses dlopen(3) in order to load
some modules.  Undefined symbols in these modules are resolved by the
dynamic linker.  If the program is linked statically, the linker has
no way of finding out which symbols are already present in the program
and might causes strange problem so that proper symbols isn't used --
Initialize function in statically linked libraries is called, and some
global variable is initialized, dynamically loaded modules might also
expects those initialized global variable."

Can this be solved with some changes to the make files, or do I need to upgrade to a newer Ubuntu and the next version of Scite?

---

### Post by NathanB on 2007-05-25
Duh... of course -- I just needed the "libgtk2.0-dev" package.

---

