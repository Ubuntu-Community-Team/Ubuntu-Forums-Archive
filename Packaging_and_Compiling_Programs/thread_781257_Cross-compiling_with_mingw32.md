---
title: "Cross-compiling with mingw32"
date: 2008-05-04
forum: Packaging and Compiling Programs
---

### Post by k_l_k on 2008-05-04
Hi,

I am using Ubuntu 6.06.2 with mingw32 installed as a cross compiler. I installed it with "apt-get install mingw32 mingw32-binutils mingw32-runtime". 

I wrote the following simple program to test whether compilation works: 

int main(int argc, char* argv[])
{
        return 0;
}


When I try compiling it, however, I get the following:

tgs@tgs-desktop:~/test$ i586-mingw32msvc-gcc simpletest.c -o simpletest.exe
/tmp/cc5xd3WR.s: Assembler messages:
/tmp/cc5xd3WR.s:2: Error: unknown pseudo-op: `.def'
/tmp/cc5xd3WR.s:2: Error: unknown pseudo-op: `.scl'
/tmp/cc5xd3WR.s:2: Error: unrecognized symbol type ""
/tmp/cc5xd3WR.s:2: Error: junk at end of line, first unrecognized character is `3'
/tmp/cc5xd3WR.s:2: Error: unknown pseudo-op: `.endef'
/tmp/cc5xd3WR.s:5: Error: unknown pseudo-op: `.def'
/tmp/cc5xd3WR.s:5: Error: unknown pseudo-op: `.scl'
/tmp/cc5xd3WR.s:5: Error: unrecognized symbol type ""
/tmp/cc5xd3WR.s:5: Error: junk at end of line, first unrecognized character is `3'
/tmp/cc5xd3WR.s:5: Error: unknown pseudo-op: `.endef'

I feel like i586-mingw32msvc-gcc is trying to pass its output to the wrong assembler. There shouldn't be a reason for this though, I have all of the required programs in my path:

tgs@tgs-desktop:~/test$ ls /usr/bin/ | grep i586
i586-mingw32msvc-addr2line
i586-mingw32msvc-ar
i586-mingw32msvc-as
i586-mingw32msvc-c++
i586-mingw32msvc-cc
i586-mingw32msvc-c++filt
i586-mingw32msvc-cpp
i586-mingw32msvc-dlltool
i586-mingw32msvc-dllwrap
i586-mingw32msvc-g++
i586-mingw32msvc-gcc
i586-mingw32msvc-gcc-3.4.4
i586-mingw32msvc-gccbug
i586-mingw32msvc-gcov
i586-mingw32msvc-ld
i586-mingw32msvc-nm
i586-mingw32msvc-objcopy
i586-mingw32msvc-objdump
i586-mingw32msvc-ranlib
i586-mingw32msvc-readelf
i586-mingw32msvc-size
i586-mingw32msvc-strings
i586-mingw32msvc-strip
i586-mingw32msvc-windres

I found some advice that told me to set the 'AS' environment variable to i586-mingw32msvc-as, but that didn't work either.

Thoughts?

---

### Post by k_l_k on 2008-05-04
I used the "-v" flag to i586-mingw32msvc-gcc to see that it was indeed invoking the default GNU assembler.

It turns out that my initial install command was incorrect. I re-installed them, and instead of requesting all of them at once, I only requested mingw32 and let the package manager sort out the dependencies (i.e. apt-get install mingw32).

After install, I re-ran the test and everything worked fine (ran the output executable on Windows).

---

