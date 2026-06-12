---
title: "Syntax woes..."
date: 2010-05-06
forum: Programming Talk
---

### Post by jwbrase on 2010-05-06
Why is it that everybody else's copy of gcc seems to use a different syntax than mine? Every once in a while I'll compile a program from source, and what apparently compiled fine for the author throws compiler errors at me. I'm not talking missing libraries or machine-specific optimizations, I'm talking plain and simple syntax errors like "static declaration of foo follows non-static declaration" and (the one that's currently bugging me) "lvalue required as left operand of assignment". It seems odd to me that what qualifies as an lvalue for an author compiling with gcc on Linux should not qualify for me, also compiling with gcc on Linux.

Does anyone know of a place where I can find a list of common gcc errors encountered when compiling somebody else's program from source, and the code tweaks that most often solve them?

---

### Post by Seal Daemon on 2010-05-06
Most of these *differences* are made by developers themselves - compile, **change something**, pack it up for the later usage ..

---

### Post by nvteighen on 2010-05-06
Well... it really depends on what you're compiling...

For instance, of you're compiling something meant to be compiled using Makefiles and/or autotools, please use that.

But, more important, who said everything published on the webs is correct? I mean, people might post code they compile, for example, without activating warnings, while you may be using -Wall and see the subtle errors/warnings these people do and don't even notice. Other source for differences may be the usage of different C standards (though I'm not sure those specific errors you posted may be related to this).

---

### Post by jwbrase on 2010-05-06
> **nvteighen said:**
> Well... it really depends on what you're compiling...

For instance, of you're compiling something meant to be compiled using Makefiles and/or autotools, please use that.

But, more important, who said everything published on the webs is correct? I mean, people might post code they compile, for example, without activating warnings, while you may be using -Wall and see the subtle errors/warnings these people do and don't even notice. Other source for differences may be the usage of different C standards (though I'm not sure those specific errors you posted may be related to this).

That's just the thing: I'm using the supplied makefiles.

Untar, make, and *boom*, syntax error. This probably happens with a good 25% of the compiles I attempt.

---

### Post by soltanis on 2010-05-06
You usually need to run ./configure before running make, at least with source code that uses the autotools system (which sucks, but anyway). A lot of authors also don't properly set the configure script to check all script dependencies, so make sure you have the right development packages installed.

---

### Post by jwbrase on 2010-05-06
> **soltanis said:**
> You usually need to run ./configure before running make, at least with source code that uses the autotools system (which sucks, but anyway). A lot of authors also don't properly set the configure script to check all script dependencies, so make sure you have the right development packages installed.

Yes, I generally do whatever the install, readme, or whatever says. I didn't mention ./configure because the last program I tried doesn't have a configure, just a Makefile.

---

