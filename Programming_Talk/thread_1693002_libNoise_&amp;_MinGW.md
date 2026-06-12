---
title: "libNoise &amp; MinGW"
date: 2011-02-22
forum: Programming Talk
---

### Post by roadkillguy on 2011-02-22
I've been attempting to cross compile an application from ubuntu to windows that uses the libnoise library.  Generally, I rename the windows library (libnoise.lib in this case) to a linux library in the /usr/i586mingw32msvc/lib folder. (libnoise.a)

Unfortunately, this hasn't worked.  It's not complaining about not finding the library, it's complaining that it cannot find the noise::Module class.

[HTML]out/BaseBlockTerrain.o:BaseBlockTerrain.cpp:(.text+0xe2b): undefined reference to `noise::module::Const::Const()'[/HTML]

Is one of the many.


Does anyone know where to find mingw libnoise libraries or what to do at this point?

Thanks

---

### Post by roadkillguy on 2011-02-23
Nobody?

---

### Post by PaulM1985 on 2011-02-24
A library that was compiled for windows can't just be renamed to use it on linux.  You need to re-compile the source code for linux.

Have you got the source code?

Paul

---

### Post by roadkillguy on 2011-02-24
Using minGW32 to cross compile for Windoze I would think that it requires .libs.

When I compile with my linux libraries my program compiles just fine.

How do I go about installing minGW libraries otherwise?  They offer next to nothing on their website.

---

### Post by PaulM1985 on 2011-02-24
Ah, I didn't see **CROSS** compile, when I first read your post.  I thought you were getting a windows lib and were trying to use it in Linux.  Sorry.

To make up I did some searching.  I have found some stuff here:

[http://libnoise.sourceforge.net/downloads/index.html](http://libnoise.sourceforge.net/downloads/index.html)

where you can download the various bits of source code.  Maybe this would help.  If you build the source using the cross compiler, you may be able to follow the steps at the bottom of this page:

[http://libnoise.sourceforge.net/tutorials/tutorial1.html](http://libnoise.sourceforge.net/tutorials/tutorial1.html)

To get it to work.

I don't really know anything about cross compilation, I just wanted to try and help since my reply was wrong in the first instance.

Good luck

Paul

---

### Post by roadkillguy on 2011-03-11
I'm still having the same problem.

I've found that when I open up vim and make a bogus libnoise.a file, it tells me I have a syntax error.  Clearly it's finding the functions and classes, but not correctly.

I'm kind of sick of mingw32 at this point.

---

### Post by SledgeHammer_999 on 2011-03-11
Did you also cross-compile libnoise? If not, you should.

---

### Post by roadkillguy on 2011-03-11
I was actually just trying that.. (unsuccessfully) though I'm not sure what it would do given that the libraries they distribute are already win32.

Should I find a 3D perlin noise function and implement it myself? I do like the wrapper classes libnoise uses though...

---

### Post by roadkillguy on 2011-03-12
Are there any other cross compilers besides mingw32 I should be using?  I have the source for libnoise, but I'm clueless as to how to build a windoze library out of it.

---

### Post by SledgeHammer_999 on 2011-03-12
> **roadkillguy said:**
> Are there any other cross compilers besides mingw32 I should be using?  I have the source for libnoise, but I'm clueless as to how to build a windoze library out of it.

None that I am aware of.

BUT a few questions.

1. Do you know how to compile already available projects from source? (the configure-make-make install cycle)? If no, learn how to do it on linux. If yes, keep reading.

2. Have you told to the configure scrpt to use the mingw-gcc and not the systems gcc? If no, then investigate on how to do it. If yes, then it must mean that "make" fails. plz post the error message in that situation. 

(do the above steps to compile libnoise from source)

NOTE: when configuring for cross-compilation you should tell the script a local installdir (eg --prefix=$HOME/cross_compile)


If you manage to compile libnoise then you must compile your application using the mingw32-gcc AND make the linker look for the libnoise libs/includes in your local installdir (mentioned above).

---

### Post by roadkillguy on 2011-03-12
I've been able to get libnoise.a generated using g++, but i586-mingw32msvc-g++ hasn't been so lucky.

```

..blablablapath..$ make libnoise.a CXX=i586-mingw32msvc-g++
libtool --mode=link i586-mingw32msvc-g++  -o libnoise.a ../src/latlon.o ../src/noisegen.o ../src/model/cylinder.o ../src/model/line.o ../src/model/plane.o ../src/model/sphere.o ../src/module/abs.o ../src/module/add.o ../src/module/billow.o ../src/module/blend.o ../src/module/cache.o ../src/module/checkerboard.o ../src/module/clamp.o ../src/module/const.o ../src/module/curve.o ../src/module/cylinders.o ../src/module/displace.o ../src/module/exponent.o ../src/module/invert.o ../src/module/max.o ../src/module/min.o ../src/module/modulebase.o ../src/module/multiply.o ../src/module/perlin.o ../src/module/power.o ../src/module/ridgedmulti.o ../src/module/rotatepoint.o ../src/module/scalebias.o ../src/module/scalepoint.o ../src/module/select.o ../src/module/spheres.o ../src/module/terrace.o ../src/module/translatepoint.o ../src/module/turbulence.o ../src/module/voronoi.o
libtool: link: unable to infer tagged configuration
libtool: link: specify a tag with `--tag'

```

EDIT: After adding --tag=CXX, I was able to get it to compile.  I'm not sure if the library was packaged correctly, because my application still didn't build after that.

Does libtool support windows libraries?

---

### Post by roadkillguy on 2011-03-15
It's still not working.. and I've even been able to get pthreads linking.
 
Is there a windows equivalent of libtool?:confused:

---

### Post by roadkillguy on 2011-03-16
Progress!! I figured out how to use i586-mingw32msvc-dlltool, and was able to compile libnoise like so:

```
i586-mingw32msvc-dlltool ../src/latlon.o ../src/noisegen.o ../src/model/cylinder.o ../src/model/line.o ../src/model/plane.o ../src/model/sphere.o ../src/module/abs.o ../src/module/add.o ../src/module/billow.o ../src/module/blend.o ../src/module/cache.o ../src/module/checkerboard.o ../src/module/clamp.o ../src/module/const.o ../src/module/curve.o ../src/module/cylinders.o ../src/module/displace.o ../src/module/exponent.o ../src/module/invert.o ../src/module/max.o ../src/module/min.o ../src/module/modulebase.o ../src/module/multiply.o ../src/module/perlin.o ../src/module/power.o ../src/module/ridgedmulti.o ../src/module/rotatepoint.o ../src/module/scalebias.o ../src/module/scalepoint.o ../src/module/select.o ../src/module/spheres.o ../src/module/terrace.o ../src/module/translatepoint.o ../src/module/turbulence.o ../src/module/voronoi.o --export-all-symbols -l libnoise.a
```

Linking to libnoise.a, (-lnoise), I was able to get the following (Much different) output.

```

fu000001.o:(.idata$2+0xc): undefined reference to `_libnoise_a_iname'
fu000004.o:(.idata$2+0xc): undefined reference to `_libnoise_a_iname'
fu000006.o:(.idata$2+0xc): undefined reference to `_libnoise_a_iname'
fu000008.o:(.idata$2+0xc): undefined reference to `_libnoise_a_iname'
fu000010.o:(.idata$2+0xc): undefined reference to `_libnoise_a_iname'
fu000012.o:(.idata$2+0xc): more undefined references to `_libnoise_a_iname' follow
nmth000000.o:(.idata$4+0x0): undefined reference to `__nm___ZTVN5noise6module6PerlinE'
nmth000022.o:(.idata$4+0x0): undefined reference to `__nm___ZTVN5noise6module6SelectE'
nmth000027.o:(.idata$4+0x0): undefined reference to `__nm___ZTVN5noise6module10TurbulenceE'
collect2: ld returned 1 exit status
make: *** [windows] Error 1
```

Can anybody interpret these errors?  I've found error handling is a learned skill.

---

### Post by roadkillguy on 2011-03-16
I've also found that adding -nostartfiles to the linker line produces similar errors.

Anybody?

---

### Post by roadkillguy on 2011-03-18
Despite your relentless effort, I seem to have solved this myself.

Rather than using any kind of libtool or dlltool, I used raw i586-mingw32msvc-g++ commands to create the library.  (I'm not really sure what those do anymore)

```
i586-mingw32msvc-g++ -shared -o libnoise.dll [A bunch of .o files] -Wl,--export-all-symbols -Wl,--out-implib,libnoise.a
```
Produced a nice libnoise.dll and libnoise.a for use with mingw and my application, which now runs fine under wine.

Thanks for... reading?  Hope this helps anybody else cross compiling ubuntu libraries for windows/mingw!

---

