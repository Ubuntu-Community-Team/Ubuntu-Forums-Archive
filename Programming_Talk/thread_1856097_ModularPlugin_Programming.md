---
title: "Modular/Plugin Programming"
date: 2011-10-07
forum: Programming Talk
---

### Post by tbastian on 2011-10-07
I've been interested in modular (as in plugin) programming for a while, and I finally have a good excuse to use it! Can anybody direct me to good resource regarding this topic?

What I need to do is convert various data formats into various other formats, and I'd like to be able to use plugins in such a way that my program can autodetect what sort of plugins are available, and implement them into my program without requiring a re-compile.

---

### Post by karlson on 2011-10-07
> **tbastian said:**
> I've been interested in modular (as in plugin) programming for a while, and I finally have a good excuse to use it! Can anybody direct me to good resource regarding this topic?

What I need to do is convert various data formats into various other formats, and I'd like to be able to use plugins in such a way that my program can autodetect what sort of plugins are available, and implement them into my program without requiring a re-compile.

Not sure what exactly you are looking for but there are plenty of different libraries/products that allow or use modules/plugins.  You can start with these:

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html)
[http://qt.nokia.com](http://qt.nokia.com)
[http://www.r-project.org](http://www.r-project.org)

As long as you understand that what you're basically writing is a small program/library that has predefined entry points specified by the calling program.

---

### Post by cgroza on 2011-10-07
In what language are you working in? I am sure there are plugin systems available for it. For example, with Python, I used Yapsy to detect and manage the plugins.

---

### Post by nvteighen on 2011-10-08
AFAIK, modular and plugin programming are two different things. Modular programming is what you should be always doing: divide your code into modules, so that each module constitutes a small and compact semantic unit. Plugin programming, instead, is about making your program able to load and run code at runtime.

Plugin programming is almost trivial in a dynamic language like Python. Check the code for PycTacToe in my sig, it basically uses a plugin-like architecture. In languages like C or C++, the way to go is by using the linker's API if have your plugins written as shared libraries or using a scripting language.

You'll have to create a plugin API, though. You have to be very careful on what the plugins will be required to have in order to be loadable and runnable. For example, in PycTacToe, among other things, all game plugins are required to have a procedure called main that accepts no arguments and returns an integer. This allows me to run any (valid) plugin by just calling plugin.main().

Managing plugins can be tricky, though. Take a look at the suggestions you've been given, but if it's a simple program, you may be fine with having a directory and reading its contents.

---

### Post by PaulM1985 on 2011-10-08
This reminds me of common object model that is used in windows. Look up common object model and see if it is the sort of thing you want.  There seems to be a simple implementation on SourceForge here [http://sourceforge.net/projects/simcom/](http://sourceforge.net/projects/simcom/).

Paul

---

