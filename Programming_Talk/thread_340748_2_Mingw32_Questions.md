---
title: "2 Mingw32 Questions"
date: 2007-01-17
forum: Programming Talk
---

### Post by Crypto-138 on 2007-01-17
I have 2 questions about mingw32 that are really confusing me at the moment:

I.)  Can the official MingW from the repositories link .lib files to dll's? Someone at [this](http://www.heroinpuppy.com/forums/YaBB.cgi?num=1166922186/0#1) forum told me you need a special Dev-C++ implementation of mingw. I used Dev-C++ on Windows, and .lib files linked perfectly. I've tried the mingw32 from the Ubuntu Repositories to no avail. I always get an ld error of some kind.
II.) If you do need the Dev-c++ Mingw32, could someone help me compile the newest version? I found [this guide](http://www.hwaci.com/sw/sqlite/mingw.html), but it's heavily outdated. 
(The page was last modified 4 years ago ](*,))

I'm trying to build the mingw source provided at Dev-C++'s [SourceForge Page](http://sourceforge.net/project/showfiles.php?group_id=10639), but if the one at [www.mingw.org](www.mingw.org) is better, and it has .lib support, I'll use that instead.

---

### Post by Crypto-138 on 2007-01-18
Eh. I solved it. I used a tool called reimp to translate the MSVC .lib file to a GCC .a file

---

