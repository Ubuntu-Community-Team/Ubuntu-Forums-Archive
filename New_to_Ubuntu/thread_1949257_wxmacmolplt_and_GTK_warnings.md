---
title: "wxmacmolplt and GTK warnings"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by chemjeff on 2012-03-29
Hi,
When I run the program wxmacmolplt (found here: [www.scl.ameslab.gov/MacMolPlt/](www.scl.ameslab.gov/MacMolPlt/)) from the terminal, when it first starts up I get the warnings:

log: Vertex shader was successfully compiled to run on hardware.

log: Fragment shader was successfully compiled to run on hardware.


and then when I close it, I get the warnings:
** (wxmacmolplt:2904): CRITICAL **: os_pager_hide: assertion `OS_IS_PAGER (pager)' failed

(wxmacmolplt:2904): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

** (wxmacmolplt:2904): CRITICAL **: os_pager_set_parent: assertion `OS_IS_PAGER (pager)' failed


Is there a way to get rid of these warnings?  Thanks!

---

### Post by PhantomTurtle on 2012-03-29
If the app opens fine, then you can just ignore the warnings. I'm not sure how to get rid of them, but I believe you can safely ignore this.

---

### Post by itsols on 2012-04-01
I get the same error just by running a BLANK form. But it runs...

Have you found THE CAUSE of this or did you just disable it. It would be good to know why this is happening.

---

