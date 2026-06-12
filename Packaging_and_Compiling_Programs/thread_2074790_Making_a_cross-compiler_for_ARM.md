---
title: "Making a cross-compiler for ARM"
date: 2012-10-22
forum: Packaging and Compiling Programs
---

### Post by devshark on 2012-10-22
Hi all,

sorry if posting in a wrong area but this seemed like the sort of place to ask this kind of question.

I'm interested in generating/building a cross-compiler for ARM.

I want my target binaries to be for ARM, and for them to be compiled on a host x86_64 machine.

I have read these links:
[http://www.ailis.de/~k/archives/19-ARM-cross-compiling-howto.html](http://www.ailis.de/~k/archives/19-ARM-cross-compiling-howto.html)
[http://www.kegel.com/crosstool/](http://www.kegel.com/crosstool/)
[http://linux.bytesex.org/cross-compiler.html](http://linux.bytesex.org/cross-compiler.html)
[http://frank.harvard.edu/~coldwell/toolchain/](http://frank.harvard.edu/~coldwell/toolchain/)

but I didn't get up-to-date information on building one. Then I found [crosstool-ng]("http://crosstool-ng.org/") script which seems to be what everyone's using but nobody really mentions it or how they're using it.

I'm hoping to get some clarifications on how to build a crosscompiler that works just like the one I have right now but that can compile on a x86/x86_64 machine (because compiling natively takes hours). Preferably in a form of a executable script, but vague theoretical answers are also ok ;) as long as they're useful and/or constructive.

Can anyone help a fellow noob out here? :) It's my first post after all.

Thanks in advance,
Shark

---

