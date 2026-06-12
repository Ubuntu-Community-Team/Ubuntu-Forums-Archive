---
title: "undefined reference"
date: 2005-09-09
forum: Programming Talk
---

### Post by neighborlee on 2005-09-09
Hi fellow programmers..

   I am trying to compile openscenegraph.org here but its failing trying to compile the OpenSceneGraph component ( made up of three pieces) with this errror:

make[3]: Entering directory `/home/neighborlee/Programming/OSG_OP_OT-0.9.9/OpenSceneGraph/applications/osgconv/Linux32.Opt'
g++  -O2 -L/usr/X11R6/lib -L../../../lib/Linux32   OrientationConverter.o osgconv.o    -lstdc++ -losgProducer -lProducer -losgText -losg -losgUtil -losgGA -losgDB -lGLU -lGL  -lOpenThreads   -o osgconv
/usr/local/lib/libProducer.so: undefined reference to `XF86VidModeQueryVersion'
/usr/local/lib/libProducer.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[3]: *** [osgconv] Error 1

checking google found a forum whereby this was suggested:
export X11_Xext_LIB=/usr/X11R6/lib/libXext.so:/usr/X11R6/lib/libXxf86vm.so< which I did, but it also suggested exporting a variable which I did to no avail..no biggie we keep pushing fwd ;-))

I verified that the libs are indeed IN that loaction and they are..

I still cant get my project to compile, getting same error as above..

any ideas ? :-0)

thx
nl

---

### Post by neighborlee on 2005-09-09
[QUOTE=neighborlee]Hi fellow programmers..

   I am trying to compile openscenegraph.org here but its failing trying to compile the OpenSceneGraph component ( made up of three pieces) with this errror:

make[3]: Entering directory `/home/neighborlee/Programming/OSG_OP_OT-0.9.9/OpenSceneGraph/applications/osgconv/Linux32.Opt'
g++  -O2 -L/usr/X11R6/lib -L../../../lib/Linux32   OrientationConverter.o osgconv.o    -lstdc++ -losgProducer -lProducer -losgText -losg -losgUtil -losgGA -losgDB -lGLU -lGL  -lOpenThreads   -o osgconv
/usr/local/lib/libProducer.so: undefined reference to `XF86VidModeQueryVersion'
/usr/local/lib/libProducer.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[3]: *** [osgconv] Error 1

checking google found a forum whereby this was suggested:
export X11_Xext_LIB=/usr/X11R6/lib/libXext.so:/usr/X11R6/lib/libXxf86vm.so< which I did, but it also suggested

I verified that the libs are indeed IN that loaction and they are..

I still cant get my project to compile, getting same error as above..

any ideas ? :-0)

thx
nl[/QUOTE]



nm I think I got it.I just had to look up makedefs in Make subDIR and add -lXext and -lXxF86vm to X_LIBS line and make clean and redo make..

in theory anyway..still compiling so we'll see ;-))

cheers
nl

---

### Post by neighborlee on 2005-09-09
[QUOTE=neighborlee]nm I think I got it.I just had to look up makedefs in Make subDIR and add -lXext and -lXxF86vm to X_LIBS line and make clean and redo make..

in theory anyway..still compiling so we'll see ;-))

cheers
nl[/QUOTE]

Yes it turned out fine..;0)

cheers
nl

---

