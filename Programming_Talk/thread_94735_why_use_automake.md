---
title: "why use automake?"
date: 2005-11-24
forum: Programming Talk
---

### Post by kreso on 2005-11-24
Why do Kdevelop and Anjuta use automake instead of simple makefiles? I mean, whenever I want to recompile the program I have to sit through all that ./configure stuff.

I realize the importance of automake when releasing a project, but why use it while you're developing it??

---

### Post by zlogic on 2005-11-25
Kdevelop uses QMake which is a lot faster for QT projects.
./configure alows you to generate makefiles using data like library/include paths, linked libraries etc. If you change something like that in your project, the makefiles will have to be heavily modified, and ./configure handles that task.

---

### Post by kreso on 2005-11-26
but basicly, for a simple project with a few source files, you don't need autoconf, right? I mean, you can just call g++ a couple of times and that's it.

---

### Post by gord on 2005-11-26
well yea but that kinda misses the point ;) automake and all that provides a (sorta) standardised way of compiling. also, it allows you to only compile what you need to compile, for example, if you have only changed moo.c and the program has hundreds of other allready compiled files that havn't changed, it will only compile moo.c

if you don't like it you can allways just edit it in anjuta or whatever and compile it through the command line. simple really.

---

### Post by kreso on 2005-11-28
okay, but aside from that, are there any other advantages of using automake for local system development?

---

### Post by Chuck Adams on 2005-11-28
I find autotools to be a rather repugnant and cumbersome hack and prefer scons by far (even if I'm not a python fan), but they have similar intents even if the approach differs.  Every "local development" and "one off" that you work on for more than, say, a month, tends to grow, and when it does, you want to have to do the least amount of futzing with the build process to make it Just Work and keep Just Working whenever you change some config item in the system or add this or that option, and so on.  At that point, you'll be happy you started with something more than an ad hoc makefile rather than going through and autoconf/automake-ifying your system later.

Personally I prefer using lots of little makefiles (which totally precludes automake), but then I run into the brain damage of make itself...

---

