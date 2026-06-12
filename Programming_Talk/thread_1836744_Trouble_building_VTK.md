---
title: "Trouble building VTK"
date: 2011-08-31
forum: Programming Talk
---

### Post by hadjimurad on 2011-08-31
Hey all, I'm having an issue building VTK. I have g++ and the mesa openGL implementation. I get the following error message:

```

Building CXX object Rendering/CMakeFiles/vtkRendering.dir/vtkGraphicsFactory.cxx.o
In file included from /home/daniel/programs/VTK/Rendering/vtkGraphicsFactory.cxx:65:
/home/daniel/programs/VTK/Rendering/vtkXRenderWindowInteractor.h:37:74: error: X11/StringDefs.h: No such file or directory
/home/daniel/programs/VTK/Rendering/vtkXRenderWindowInteractor.h:38:73: error: X11/Intrinsic.h: No such file or directory

```

I think it's looking in the wrong place for X11; it's looking for X11/(some stuff).h, when maybe it should be looking under /usr/bin/X11 or /usr/lib/X11? Anyhow, any help would be appreciated.

---

### Post by Zugzwang on 2011-09-01
> **hadjimurad said:**
> 
I think it's looking in the wrong place for X11; it's looking for X11/(some stuff).h, when maybe it should be looking under /usr/bin/X11 or /usr/lib/X11? Anyhow, any help would be appreciated.

Look here: [http://packages.ubuntu.com/search?searchon=contents&keywords=Intrinsic.h&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=Intrinsic.h&mode=exactfilename&suite=natty&arch=any) - If you have the package "libxt-dev" installed, there is a file named "/usr/include/X11/Intrinsic.h" on your system. As "/usr/include" is a default path in which the compiler looks when searching for a header file, "X11/Intrinsic.h" will be found relative to that path. So my guess is that you don't have all the necessary packages installed, in particular not "libxt-dev".

---

