---
title: "Use --disable-werror without configure?"
date: 2008-10-12
forum: Packaging and Compiling Programs
---

### Post by FranMichaels on 2008-10-12
Alright, I've been stumped on this. Trying to compile sdlmess on Ubuntu 8.10 beta (current dist-upgrade) with gcc 4.3.

I tried to rebuild what I had. failed, then pulled from the svn repo of sdlmess failed.

The problem is, it's treating warnings as errors.

--disable-werror 

Should fix it, but sdlmess provides a Makefile.sdl sans a configure script :(

I've tried passing different make parameters, like -k and -b. No help...
I've searched all over so I apologize if this has come up, but what values in the Makefile need to be changed, or is there a way to set a system wide option to treat warnings as just warnings. 

I just love compiling, as I'm not debugging I'd really prefer the warnings ignored...

Thanks in advance!
:KS

---

### Post by FranMichaels on 2008-10-13
*BUMP* 
Come on ladies and gents someone must have run into this...

---

