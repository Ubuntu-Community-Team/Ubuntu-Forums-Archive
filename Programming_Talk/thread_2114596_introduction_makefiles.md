---
title: "introduction makefiles"
date: 2013-02-10
forum: Programming Talk
---

### Post by thedardanius on 2013-02-10
hey,

Im a windows programmer trying to learn this wonderful world of linux... at least linux distros using x lib.
I constantly am confronted with makefiles, when reading papers on gcc compiling. Can sb give me a gentle introduction of makefiles, and their uses/purposes? please note im very very new to gcc world of compiling. Im really used to Visual studio ;p

---

### Post by TheFu on 2013-02-10
Makefiles are another language specifically designed to build only certain parts of a program when necessary.  Because they are pure text files, modifying the settings is trivial and fast.  Ensuring that different parts of a program have identical settings is easy too.

gmake (and other make tools) have built-in rules that support compiling and linking commonly seen file types. As an example, "**.c.o:** " says that all C program files build into .o (object files).  It is possible to specify manually which exact files are compiled too.

**.h.c: **
says that **file.c** is dependent on **file.h**.  So if file.h changes, the timestamp is newer, then the file.c needs to be recompiled.  The same applies for the .o file - if the .c file is newer.  In this way, only those files that need to be recompiled due to dependencies are. This is much more efficient than manually creating a compile script.

Since dependencies are seldom simple, most compilers have a way to ask for dependencies which can be placed into another file or appended to the bottom of the Makefile though scripting.  **gcc -MM **does this for gcc, I believe.  In the old days, we used a tool called **makedepend**.

Makefiles are not limited to just compiling.  Anything that can be scripted can be managed through make.  Library creation, test runs, lex, yacc, bison, idl, SQL, packaging, old file cleanup, C-Lint runs, documentation builds, along with compiling and linking too.

You need to learn to walk before you learn to run, so a simple makefile is probably best to begin.  Also, know that spaces are slightly important and **{tabs} are critical**, so the editor you use while editing a Makefile is critical. If it swaps tabs for spaces or spaces for tabs, you are screwed.

Visual Studio is an amazing tool, but it has warped you for all other programming. ;)

That's a gentle introduction.

Having someone knowledgeable talk you through a simple makefile is the best way to learn.

---

