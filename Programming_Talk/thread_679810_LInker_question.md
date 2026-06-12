---
title: "LInker question"
date: 2008-01-27
forum: Programming Talk
---

### Post by skullmunky on 2008-01-27
I'm trying to build an executable, let's call it E  iit relies on a static library, A,  compiled earlier in the build process, which itself relies on a shared library, S.  At compile time the linker can't resolve symbols in A that are from S.  

err, maybe a concrete explanation is better than an abstract one.

i'm trying to build the panda3d on ubuntu 7.04.  ([www.panda3d.org](www.panda3d.org))

part of it is a converter utility that converts maya files to panda's "egg" 3D model format.  while panda is cross-platform, the maya util has only been built on windows before; everything -should- work, i'm just having this fiddly linker problem.

the app i'm building is called "maya2egg".  it uses a library called "libmaya85.a", which is, I think, a kind of interface layer that the panda build system makes to talk to maya.    

here's the error:

```

built/lib/libmaya85.a(maya85_composite1.o): In function `MayaApi::~MayaApi()':
maya_composite1.cxx:(.text+0x1de3): undefined reference to `MLibrary::cleanup(int)'

```

and here's the link command (tidied up a bit for ease of reading):

```

g++ -o built/bin/maya2egg85-wrapped 
-Lbuilt/lib -L/usr/X11R6/lib 
built/tmp/maya2egg85_mayaToEgg.o 
built/lib/libmayaegg85.a built/lib/libmaya85.a built/lib/libeggbase.a
built/lib/libprogbase.a built/lib/libconverter.a built/lib/libpandatoolbase.a 
-lpandaegg -lpanda -lpandaexpress -lp3dtoolconfig -lp3dtool -lp3pystub
-L/usr/autodesk/maya8.5/lib 
-Wl,-rpath,/usr/autodesk/maya8.5/lib 
-Wl,-rpath-link,/usr/autodesk/maya8.5/lib 
-lFoundation -lOpenMaya -lOpenMayaAnim -lOpenMayaUI -lpthread

```

I feel like there's some other flag or something that ld needs ... but not sure what it would be.  

earlier on when libmaya85.a is built, I don't get any errors; does it not try to resolve external symbols at that point?

---

### Post by geraldm on 2008-01-27
At the time that the final application is compiled and linked, the order of the libraries is to load the shared libraries first, then the app, and finally the static libraries.
Check that the 'MLibrary::cleanup(int)' is defined in the shared libraries that you have declared.

External references are not checked when building a library, but left to when the library is linked into the application.

Gerald

---

### Post by skullmunky on 2008-01-28
thanks gerald.  good, so it does work the way i thought.  and you're right, the symbol is not in fact in that library at all - I thought it would be in libOpenMaya.so.  It's actually in libOpenMayalib.a.  ???? well, when I get home I'll try that out :) 

not crucial, but i'm sort of curious - to find out if this was the problem, i used nm, which told me that the .so files have no symbols in them.  how is that possible?

---

