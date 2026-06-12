---
title: "Makefiles in development process"
date: 2007-03-06
forum: Programming Talk
---

### Post by Curtisc on 2007-03-06
I haven't worked with makefiles before, so please bear with me.  There's an open source project that I'd like to mess around with, but do I need to run through all the steps of the makefile every time I make a little change?  It is a relatively small program but it still takes ~5-10 minutes to compile and build on my computer.  Is there some way I check to see what code was modified and only compile those files, or skip dependency checking, or something?

---

### Post by lnostdal on 2007-03-06
while make doesn't provide built-in automatic dependency checking/generation (and thus only compilation of changed files) there is a "hack" you can do to get this using make: [http://www.gnu.org/software/make/manual/make.html#Automatic-Prerequisites](http://www.gnu.org/software/make/manual/make.html#Automatic-Prerequisites)

i strongly recommend using a better build-tool than make when you have the opportunity .. scons works well for me (see my sig. for a link to a short guide about scons)

in some cases however the nature of c/c++ makes even trivial changes in the code trigger massive recompilation regardless of what build-tool you use or whatever you do .. you might consider things like ccache (caches stuff like dependency checking etc.) and distcc in these cases

---

