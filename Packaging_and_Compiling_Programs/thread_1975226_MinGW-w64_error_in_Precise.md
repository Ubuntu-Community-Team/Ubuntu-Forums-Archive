---
title: "MinGW-w64 error in Precise"
date: 2012-05-07
forum: Packaging and Compiling Programs
---

### Post by qyot27 on 2012-05-07
I don't really think this is a 'bug', per ce, but there was a change in the way the repository versions of MinGW-w64's compilers were built, and now I'm getting build errors in one of the projects I follow.  The same project builds fine in previous releases.

From what I can tell (through the use of [i686-w64-mingw32-]gcc -v), the difference that causes the issue is that the build in Precise's repositories uses --enable-shared (this is mentioned as a fix on Launchpad so that shared versions of libgcc and libstdc++ are provided).  The build for Oneiric and - I presume, since they also worked correctly - previous releases used --disable-shared.  Due to issues with this, the link phase completely fails with exception handling-related errors or causes builds that manage to actually compile to need extra .dlls that a static build should not be requiring.  Furthermore, -static-libgcc and/or -static-libstdc++, the options suggested to avoid the problem, get ignored or cause build errors because they aren't getting applied consistently (this part might be a bug).

Some things (like FFmpeg and x264) can be tricked into using the correct static libraries by moving all the *.dll.a in /usr/lib/gcc/i686-w64-mingw64/4.6 to a subdirectory so that they can't see them and use them mistakenly.  However, for some things I have to build as shared libraries (FFMS2, in AviSynth C plugin form), this tactic doesn't work, leaving me with the problem described above.

Unfortunately, it looks like the only way for me to be able to get around this is to rebuild MinGW-w64's gcc and g++ myself, and make sure I use --disable-shared.  I don't want to do that, especially because it would probably take days to complete on this computer (also because I've never had to build gcc before).  If there is something that might be able to resolve this without rebuilding gcc, I'd like to know.

---

### Post by qyot27 on 2012-05-21
Marked as solved since the only way I could manage to get around these problems was by re-building gcc.  Several different methods used (including attempts at tweaking the source package from the repositories) and the only thing that worked was finally using Zeranoe's build script to compile a fully static version.

Also, it turns out that with the build script it only took 6 hours to complete, and that included binutils and some other things.

---

