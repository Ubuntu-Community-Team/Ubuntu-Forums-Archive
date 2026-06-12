---
title: "Problem with OpenGL GLX"
date: 2009-10-21
forum: Packaging and Compiling Programs
---

### Post by sob123 on 2009-10-21
Hello all, just joined in :)

I am having a problem 

Installed gr_monitor and could not run it. I paste what I got below.

root@mineown-laptop:~# gr_monitor 

Gr_Monitor Version 0.80
Press the middle mouse button for key summary.
Starting up...
Segmentation fault
freeglut (gr_monitor): OpenGL GLX extension not supported by display ':0.0'

Any Idea?
Thanks

---

### Post by sob123 on 2009-10-22
Solved the problem with nvidia driver  Now gr_monitor does not complan about "OpenGL GLX extens"   BUT!  Now it gives the folowing output  root@mineown-laptop:~# Gr_Monitor Version 0.80 Press the middle mouse button for key summary. Starting up... Segmentation fault   Any idea? ThReally frustrating for me.  One question regarding gr-mointor,  Could gr-monitor give me the resource utilization graphs(CPU+MEMORY e.t.c,) on a per-process basis or could I focus on any one process and get the utilization graphs? If not please let me know if there is one.  Thanks in adcanve :)

---

### Post by dinxter on 2009-10-24
hi there, 'Packaging and Compiling'  is probably not the best forum to get help with this sort of thing. You'll probably get more advice in one of the main support forums for this kind of problem

---

