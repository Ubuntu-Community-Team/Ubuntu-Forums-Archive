---
title: "Trouble installing x86-mingw32-build-1.0 on Ubuntu 12.04"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by SepherImorth on 2012-05-26
I downloaded mingw32 to install, and navigated to the x86-mingw32-build-1.0 folder in the terminal. I type "sudo bash x86-mingw32-build.sh i686-pc-linux-gnu", type in my password, and follow the guiding prompts for the installation. I then proceed to watch a lot happen in a short time, until it throws me an error, which looks like this:

"cc1: all warnings being treated as errors
make[4]: *** [elf32-i386.lo] Error 1
make[4]: Leaving directory `/home/sepherimorth/tmp/mingw-3.4.5/binutils-2.19.1/build/bfd'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/sepherimorth/tmp/mingw-3.4.5/binutils-2.19.1/build/bfd'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sepherimorth/tmp/mingw-3.4.5/binutils-2.19.1/build/bfd'
make[1]: *** [all-bfd] Error 2
make[1]: Leaving directory `/home/sepherimorth/tmp/mingw-3.4.5/binutils-2.19.1/build'
make: *** [all] Error 2
x86-mingw32-build.sh: unrecoverable error building binutils"

If I haven't given the right info, please tell me what I missed, or what I'm doing wrong. Any and all help is very much appreciated!

---

