---
title: "Segmentation Fault in GEDIT?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by neurostu on 2008-04-27
Using GEdit in hardy has yielded a lot of errors, for me.  I've tried a couple of operations which all crash the program.

```

slayton@stockton-mini:~$ gedit

(gedit:7985): GLib-GObject-WARNING **: IA__g_object_new_valist: object class `GThemedIcon' has no property named `names'

(gedit:7985): GLib-GIO-CRITICAL **: g_themed_icon_constructed: assertion `themed->names != NULL && themed->names[0] != NULL' failed

(gedit:7985): GLib-CRITICAL **: g_strv_length: assertion `str_array != NULL' failed
Segmentation fault
slayton@stockton-mini:~$ gedit
Segmentation fault

```

These seg faults happen when I use 'open' or try to 'save as'

i never had these issues in gutsy.
 Any clues?

---

### Post by neurostu on 2008-04-28
*bump

---

### Post by Tatty on 2008-04-28
Run a test on your ram.

Reboot then select memtest from the grub menu

---

### Post by dearingj on 2008-04-28
Have you tried reinstalling gedit and/or libglib2.0-0? Does this happen in other programs as far as you know?

Open Synaptic, find gedit, right click and choose "Mark for reinstallation", then click apply

---

### Post by neurostu on 2008-04-28
Tatty: Run a test on my ram? My ram is brand new, plus I never have this problem in Gutsy, only Hardy.  What would a test on my ram reveal?

dearingj: i have had this problem in other programs (Again only in hardy though). When I try to open or save files in other programs I will sometimes get random crashes.

---

### Post by dearingj on 2008-04-28
Even new RAM can go bad, and if that is what's happening, you want to know about it before it causes any major problems.

I think it is more likely to be a corrupted file, which is why I recommended reinstalling libglib2.0-0.

---

