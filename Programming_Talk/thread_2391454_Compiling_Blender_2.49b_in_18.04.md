---
title: "Compiling Blender 2.49b in 18.04"
date: 2018-05-09
forum: Programming Talk
---

### Post by &amp;KyT$0P# on 2018-05-09
I still need to use the old Blender version 2.49b for some stuff.  I got it working in 16.04 by patching the source to compile under 16.04's gcc 5, self-compiling it, and grabbing the MESA libs and [FONT=Courier New]blender-softwaregl[/FONT] script from the official Blender 2.49b Linux64 tarball.  Unfortunately the same binary doesn't work in 18.04 due to missing libpng12, so I'm trying to rebuild in 18.04.  While I can get it to compile with gcc 5 in 18.04, the result incorrectly draws black background in various parts of the interface, making it unusable.

Some investigating suggests the problem could be 18.04's gcc 5 making -fPIC and -fPIE flags default.  If I add -fPIC to CCFLAGS, the build on 16.04 is broken in the same way as in 18.04.  So I thought adding [FONT=Courier New]-fno-PIE -no-pie -fno-PIC[/FONT] to CCFLAGS would fix it in 18.04...but it doesn't help.

I looked into compiling with clang, but patching the source code to successfully do that seems beyond my current (very limited) knowledge of C/C++.

How to get Blender 2.49b to work in 18.04?

---

### Post by &amp;KyT$0P# on 2018-05-25
bump

---

### Post by &amp;KyT$0P# on 2018-06-29
Luckily it turned out libpng12 was the only missing library, so I was able to compile that under 18.04 and that got my existing working build of Blender 2.49b running.

However I would still like to know how to compile a working build of Blender 2.49b in 18.04?

---

