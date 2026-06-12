---
title: "Feisty-&gt;Gutsy upgrade and now problem linking 32bits DSOs"
date: 2007-11-28
forum: Packaging and Compiling Programs
---

### Post by gga73 on 2007-11-28
After an upgrade from feisty to gutsy on amd64, I am now getting problems linking DSOs in 32bits (was working fine before).

It seems the compiler is picking the wrong crtbegin/end, but unsure where that is set.



Linking CXX shared library ../../../../../lib/mentalray34/exr_shader.so
cd /home/gga/code/Maya/mrLiquid/BUILD/Linux-2.6.22-14-generic-32/Release/tmp/7.0/mrClasses/GGShaderLib/src && /usr/local/bin/cmake -E cmake_link_script CMakeFiles/exr_shader.dir/link.txt --verbose=1
/usr/bin/c++  -fPIC   -O3 -DNDEBUG -m32 -L/lib32 -L/usr/lib32 -export-dynamic --whole-archive -Bsymbolic  -shared -Wl,-soname,exr_shader.so.0.2 -o ../../../../../lib/mentalray34/exr_shader.so.0.2 "CMakeFiles/exr_shader.dir/gg_exr_standalone.o" -L../../mrLibrary -L/usr/autodesk/maya7.0/devkit/mentalray/include/../lib -L/home/gga/code/Maya/mrLiquid/BUILD/Linux-2.6.22-14-generic-32/Release/lib/mentalray34 -L/usr/local/lib -lIlmImf -lImath -lIex -lHalf -lIlmThread
/usr/bin/ld: i386:x86-64 architecture of input file `/usr/lib/gcc/x86_64-linux-gnu/4.1.3/crtbeginS.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `/usr/lib/gcc/x86_64-linux-gnu/4.1.3/crtendS.o' is incompatible with i386 output
collect2: ld returned 1 exit status

---

