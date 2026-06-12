---
title: "ClanLib-0.7.8 install Error!!!"
date: 2005-09-03
forum: Programming Talk
---

### Post by grofaz on 2005-09-03
I'm getting the following build error when I run sudo "make install".

display_mode.cpp:24:38: X11/extensions/xf86vmode.h: No such file or directory
display_mode.cpp: In static member function `static std::vector<CL_DisplayMode,
   std::allocator<CL_DisplayMode> >& CL_DisplayMode::get_display_modes()':
display_mode.cpp:106: error: `XF86VidModeQueryExtension' undeclared (first use
   this function)
display_mode.cpp:106: error: (Each undeclared identifier is reported only once
   for each function it appears in.)
display_mode.cpp:110: error: `XF86VidModeModeInfo' undeclared (first use this
   function)
display_mode.cpp:110: error: `vmodes' undeclared (first use this function)
display_mode.cpp:113: error: `XF86VidModeGetAllModeLines' undeclared (first use
   this function)
make[2]: *** [display_mode.lo] Error 1
make[2]: Leaving directory `/home/kudu/Projects/ClanLib-0.7.8/Sources/Display'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/kudu/Projects/ClanLib-0.7.8/Sources'
make: *** [install-recursive] Error 1

The file "display_mode.cpp" appears to be missing. Is this a bug or am I doing something wrong ??

Regards,
grofaz

---

### Post by Jave27 on 2005-10-06
I know this message is a bit old, but you can fix it by running:

```
apt-get install libxxf86vm-dev
```

You may also need:

```
apt-get install libxmu-dev libjpeg-dev libpng-dev libogg-dev libvorbis-dev libmikmod
```

---

### Post by rn0dal on 2005-10-29
Well it is always good to have the answer to a problem. That way if someone has the same question thet know what to do.;) 

-r

---

