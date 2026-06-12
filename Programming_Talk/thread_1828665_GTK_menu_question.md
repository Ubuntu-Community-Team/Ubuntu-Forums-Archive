---
title: "GTK menu question"
date: 2011-08-19
forum: Programming Talk
---

### Post by nickos on 2011-08-19
how can i add these extra characters next to a menu item?

EG :

i create the following:

file
|
 -> Open
 -> Quit

how can i make it look like this :

file
|
 -> Open  Ctrl + 0
 -> Quit    Ctrl + Q


thanks :D

---

### Post by Smart Viking on 2011-08-19
You can do that with gtk.AccelGroup

There was a tut in a magazine about it, I'll just copy in here the code you need:
```
accelgroup = gtk.AccelGroup()
window.add_accel_group(accelgroup)
key,mod = gtk.accelerator_parse("<Control>Q")
quit_item.add_accelerator("activate",accelgroup,key,mod,gtk.ACCEL_VISIBLE)
```

---

### Post by nickos on 2011-08-19
thanks for your reply,but it is GTK+ in C.

---

### Post by JupiterV2 on 2011-08-19
Read the GTK+ C API. The code is essentially the same but with the C API. You should be able to translate the example into C fairly easily (hint, you'll need to look at the docs on Accelerator Groups, Windows and Widgets). A simple search in your browser for 'accel' under each of the listed docs will get you want you want. Struggle with it for a bit and if you can't get code to work, post it, and we'll see if we can help point you in the right direction.

---

