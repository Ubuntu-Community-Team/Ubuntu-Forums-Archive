---
title: "Gnome programming - Bonobo"
date: 2007-12-27
forum: Programming Talk
---

### Post by haelters on 2007-12-27
I'm checking out Gnome with it's different technological subparts. Bonobo is one of them. I can find it in the overview of the Gnome platform ([http://library.gnome.org/devel/platform-overview/stable/](http://library.gnome.org/devel/platform-overview/stable/)). In the development references, however, it is marked as 'about to be deprecated'. I can not find the new technology they will be using. A part will be replaced by DBus, but the rest (such as for creating panel applets), I can not find an alternative.

Could someone direct me the more doc ?

Thanks!

---

### Post by samjh on 2007-12-27
The issue with Bonobo is still under debate, I think.

Bonobo will continue to be supported in the 2.x branch of Gnome, but don't expect it to survive when Gnome eventually reaches 3.x.

Currently most of Bonobo's capabilities can be found in D-Bus.  Not all of Bonobo's capabilities have been implemented in alternative libraries.

---

