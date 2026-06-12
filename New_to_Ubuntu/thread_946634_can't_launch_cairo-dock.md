---
title: "can't launch cairo-dock"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Dfairlite on 2008-10-13
ubuntu menu button on cairo dock doesnt work

---

### Post by ajmorris on 2008-10-14
hi there,
can you please start cairo-dock from a terminal (Application --> Utilities --> Terminal) then try to click on the start menu button, and post any output here.
 
 
AJ

---

### Post by eternalnewbee on 2008-10-14
Hi ajmorris.
So how do you start it from the terminal? What should you type?

---

### Post by NewJack on 2008-10-14
Type this into the Terminal:

```
cairo-dock
```

Then if it fails to start, copy and paste the output here so others can review the error messages.

---

### Post by eternalnewbee on 2008-10-14
Thanks NewJack.
It works, but I must say it looks really ugly.
Here's the output:
nadia@nadia:~$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:123)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.

And here's what I mean by ugly:

---

### Post by ajmorris on 2008-10-14
> **eternalnewbee said:**
> Thanks NewJack.
It works, but I must say it looks really ugly.
Here's the output:
nadia@nadia:~$ cairo-dock
warning : (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263) 
while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning : (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:123) 
This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
 
And here's what I mean by ugly:
 
to remove the black border, your WM/DE must be composited. I.E. you must be running a composite manager, such as compiz or xcompmgr.  Do you have the same problem as Dfairlite that your start menu button doesnt work? if so, can you please click on the start menu button, and post the output from the terminal.
 
 
AJ

---

### Post by eternalnewbee on 2008-10-14
AJ,
not the same problem. can not run compiz, but have xcompmgr installed.
The button works, but I don't know how to post the output from the terminal.
Btw, after I posted the first output, I got more warning messages...

---

### Post by ajmorris on 2008-10-14
> **eternalnewbee said:**
> AJ,
not the same problem. can not run compiz, but have xcompmgr installed.
The button works, but I don't know how to post the output from the terminal.
Btw, after I posted the first output, I got more warning messages...
 
If you can't run compiz, feel free to start a new thread, and i'll gladly take a look at it, to get it working for you :) but as for xcompmgr, if you just press alt+f2 and type xcompmgr into it, and press enter, this will composite your WM/DE (providing your graphics allow direct rendering, otherwise you can tweak it for indirect rendering)
This will erase the black border around the dock.  As for the warning messages, don't worry about them, they are just warnings.
 
AJ

---

### Post by eternalnewbee on 2008-10-14
Thanks AJ. It worked. And I'm going to start a new thread, regarding compiz.
Appreciate your help.

---

### Post by NewJack on 2008-10-14
Make sure to check out all of the options with Cairo Dock to really personalize it.  I switched to Cairo Dock from AWN and haven't looked back

---

### Post by eternalnewbee on 2008-10-14
Thank you too, NewJack for your help.

---

### Post by overdrank on 2008-10-14
Well just highjack a thread  :)

---

### Post by eternalnewbee on 2008-10-14
Hi overdrank,
was that against the rules?..
In that case I do apologise. That wasn't my intention.

---

### Post by overdrank on 2008-10-15
> **eternalnewbee said:**
> Hi overdrank,
was that against the rules?..
In that case I do apologise. That wasn't my intention.

Its ok by me just making a observation :)
Not to mention the joke of 
> Thank you too, **NewJack** for your help.
Then Highjack.  :)

---

