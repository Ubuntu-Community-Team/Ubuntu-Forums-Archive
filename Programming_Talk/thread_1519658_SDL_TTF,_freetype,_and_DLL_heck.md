---
title: "SDL_TTF, freetype, and DLL heck"
date: 2010-06-28
forum: Programming Talk
---

### Post by EMR on 2010-06-28
I have to hand it to the authors of freetype-when you have incorrectly set up your include<>s, it jumps to detailed comments that help you figure out what you did wrong.  Helpful, though, only if you happen to be good at C++ programming and compiling, which I'm not.

So, the bottom line: how do you change "linker search paths" or whatever you call them in code::blocks for Ubuntu?  How do you link against libfreetype?

(Thanks, hope I haven't put this in the wrong place)

---

### Post by Zugzwang on 2010-06-29
Have a look at the screenshot at [http://wiki.codeblocks.org/index.php?title=Using_SDL_with_Code::Blocks](http://wiki.codeblocks.org/index.php?title=Using_SDL_with_Code::Blocks) - that page describes the process for windows, but it looks like you need to do that in the "Project Build Options".

---

