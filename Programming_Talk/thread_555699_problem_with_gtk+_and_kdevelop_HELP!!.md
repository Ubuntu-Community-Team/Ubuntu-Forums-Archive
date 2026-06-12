---
title: "problem with gtk+ and kdevelop HELP!!"
date: 2007-09-20
forum: Programming Talk
---

### Post by Samuelito on 2007-09-20
Hi to all. I'm trying to run a simple code with gtk in kdevelop starting with the hello world template. The problem is it can't find gtk/gtkgl.h. Looking in this forum someone put as response to add in both CPPFLAGS and LDFLAGS the string:
`pkg-config --cflags --libs gtk+-2.0`
But it doesn't seem to work for me.

I've installed the packages with Synaptic packet manager (which I don't know if it could be the problem). And the gtkgl.h file is located in
/usr/include/gtkglext-1.0/gtk/gtkgl.h

If in the code I change the line:
#include "gtk/gtkgl.h"
with the complete path:
#include "/usr/include/gtkglext-1.0/gtk/gtkgl.h"

It finds it but not the headers included in gtkgl.h file: gdkgl.h,gtkgldefs.h ....

Which are also there but I don't think the solution is to add all paths in the include tags.

Anyone could tell me what could I do to make it work or what I'm doing wrong? I'm a bit desperated. Any help will be greatly wellcomed.

---

### Post by thetejon on 2007-09-23
I'm having the same problem.  I know you can make a virtual directory (Not sure if that's what they're called), so that gtk/ would point to gtk-2.0/gtk, but I don't think that's the solution.

---

### Post by Samuelito on 2007-09-24
I read in another forum that a symbolic link is needed but it doesn't seem to work either. I tried from the shell:
>ln -s gtk-2.0/gtk/ gtk
but still nothing

---

