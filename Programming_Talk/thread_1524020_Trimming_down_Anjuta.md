---
title: "Trimming down Anjuta"
date: 2010-07-04
forum: Programming Talk
---

### Post by sw0rn on 2010-07-04
Ciao all,
Ubuntu 10.04 newb; extraordinarily excited at how excellent Ubuntu is and extremely disappointed I hadn't come over sooner (from Windoze). 

I'm using Anjuta currently and several things have come to my attention:

[LIST=1]
[*]When compiling/executing, Anjuta runs through all sorts of things, taking ~40-60seconds to compile and execute. Is there any way I can trim this down?
[/LIST]
[INDENT]
[LIST]
[*]During the build for a helloWorld test, I think I had ~130 messages; this took what I feel is too long to build.
[/LIST]
[/INDENT]
[LIST=1]
[*]In a project, I have *so* many files! Is there any way I can trim projects down to just one or two files (.h & .cpp)? I don't necessarily need a changeLog, readMe, or a toDo list.
[/LIST]
[INDENT]
[LIST]
[*]I'm used to using Visual Studio 08 C++ express ed., if this helps explain what kind of environment I'm use to working in.
[/LIST]
[/INDENT]I'm a very inexperienced programmer and I'm used to brute-forcing my way through school projects (when I get helplessly stuck). Fast compilation and execution would definitely increase productivity for me.

Thanks in advance for any and all responses.:)

---

### Post by MadCow108 on 2010-07-04
anjuta's build system is based on autotools and pkg-config. Both are not very good at minimizing build times and dependencies especially when machine generated.
I think by default it includes links all the gtk stuff in which takes a high amount of time.
try removing all libraries you do not need.

For learning you do not need all this autotools stuff.
Stick to plain makefiles or command line building with gcc.
This is very fast and the skills learned when doing this will help you greatly when understanding the more complex build system like autotools or cmake.

A editor/IDE suitable for this task is geany. It is very minimalistic but has the most important features and its orders of magnitude faster than anjuta (at least on slower pcs like mine ;) ).
But you need to write your own makefile for more complex builds.

---

### Post by Milliways on 2010-07-04
I agree with an earlier comment, and suggest Geany.
This is much easier for single file projects and convenient while you are learning/experimenting - you don't need a separate directory/project for each program.

Having said that, Anjuta should not take so long.
After the initial compilation, it uses make to rebuild only changed files.

The messages (which list every step) can be safely ignored, just check warnings and errors.

Even with a large multi-file project, I use Geany with a custom makefile for development/testing, and Anjuta to build/install. The source files in the Geany project directory are linked to the Anjuta src directory.

---

### Post by sw0rn on 2010-07-06
Thanks all for the speedy thorough replies. I've installed Geany and it's wonderful. Perhaps when I am advanced enough for it, I will use Anjuta. 

Although I've marked this thread as solved, is there an AutoComplete or Intellisense equivalent for Geany?

---

### Post by MadCow108 on 2010-07-06
no real "intellisense" but at least auto completion of already typed words (but without or very little context):
preferences -> editor -> completion
nevertheless its enough for smaller projects

---

