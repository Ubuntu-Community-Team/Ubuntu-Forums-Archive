---
title: "Gdk 3:  reserving screen-space"
date: 2011-05-25
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-05-25
Hi there,

I'm trying to figure out how to reserve screen space with Gtk/Gdk 3 using PyGI.
With Gtk 2 (using PyGtk) it looked like:
```
gtk.Window.get_toplevel().window.property_change("_NET_WM_STRUT",
"CARDINAL", 32, gtk.gdk.PROP_MODE_REPLACE, [0,0,24,0])
```

Now using PyGobject I have no "window" attribute and i can't call the Gdk.property_change() function and cannot trace it by introspecting (alghough it should be there now according to the [C documentation]("http://developer.gnome.org/gdk3/3.0/gdk3-Properties-and-Atoms.html#gdk-property-change"))

Is there any one who can help?
Thanks

---

### Post by cgroza on 2011-05-25
I will try a shot in the dark.
Try casting the PyGObject to GdkWindow.

---

### Post by jesuisbenjamin on 2011-05-26
> **cgroza said:**
> I will try a shot in the dark.
Try casting the PyGObject to GdkWindow.

Hi thanks. I'm not sure to understand what this means :\

---

### Post by jesuisbenjamin on 2011-05-30
Hello again,

Well after looking around and corresponding on some mailing lists, i found out there is no way currently to get X to reserve screen-space for an application using PyGI, nor is there [using PyQt]("http://ubuntuforums.org/showthread.php?t=1753131").

All my research point back to using Python-Xlib. But then this library has no documentation and no doc-string.

Has any one of you some experience with Python-Xlib? Where should I look for Window Management?

Thanks,
Benjamin

---

