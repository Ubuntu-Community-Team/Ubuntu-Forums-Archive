---
title: "Compiling ClanLib-0.7.8 Error!! Help Please!!"
date: 2005-10-08
forum: Programming Talk
---

### Post by kudu on 2005-10-08
Getting the following error when running make:

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
make[2]: Leaving directory `/home/kudu/ClanLib-0.7.8/Sources/Display'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kudu/ClanLib-0.7.8/Sources'
make: *** [all-recursive] Error 1

This line appears to be the culprit:

display_mode.cpp:24:38: X11/extensions/xf86vmode.h: No such file or directory

I checked /etc/X11 but there's no folder called "extensions" and no file called "xf86vmode.h"

What is it and where do I get it ? Is there a package missing or something ?

Thanks for any help!

Regards,
kudu


Problem Solved! Please disregard.

---

### Post by revanthedarth on 2008-01-24
I had the same problem too. For those who have the same problem, 
```
sudo apt-get install libxxf86vm-dev 
```

---

### Post by eviljoel on 2010-05-07
Thanks.  Just what I was Googling for.

- EJ

---

