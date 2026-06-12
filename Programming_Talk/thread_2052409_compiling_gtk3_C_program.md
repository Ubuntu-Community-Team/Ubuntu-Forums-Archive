---
title: "compiling gtk3 C program"
date: 2012-09-03
forum: Programming Talk
---

### Post by Hairy_Palms on 2012-09-03
im porting an old gtk2 app to gtk3 atm, and im pretty much finished, but the compiling stage is having some issues, this is the error i am getting

```
mike@mike-H55-UD3H:~/Downloads/portapp/src$ gcc main.c gui.c funcs.c -o appingtk3 `pkg-config --cflags --libs gtk+-3.0 gdk-pixbuf-2.0` -lsensors
gui.c: In function ‘start_gui’:
gui.c:467:10: warning: assignment makes pointer from integer without a cast [enabled by default]
/tmp/cczglTMu.o: In function `draw_digits':
gui.c:(.text+0x1a2): undefined reference to `gdk_draw_drawable'
/tmp/cczglTMu.o: In function `expose_event_callback':
gui.c:(.text+0x24e): undefined reference to `gdk_window_clear_area'
gui.c:(.text+0x333): undefined reference to `gdk_draw_drawable'
gui.c:(.text+0x44a): undefined reference to `gdk_draw_drawable'
gui.c:(.text+0x52f): undefined reference to `gdk_draw_drawable'
/tmp/cczglTMu.o: In function `start_gui':
gui.c:(.text+0x121e): undefined reference to `gtk_widget_get_colormap'
collect2: ld returned 1 exit status
```

does anyone know why it cant find the functions even though gdk-pixbuf is already there?

---

### Post by SledgeHammer_999 on 2012-09-03
Show us your full compilation command. The errors show that it fails at the linking stage. It probably doesn't find the correct libraries.

---

### Post by Hairy_Palms on 2012-09-04
> gcc main.c gui.c funcs.c -o appingtk3 `pkg-config --cflags --libs gtk+-3.0 gdk-pixbuf-2.0` -lsensors

thats my full compilation command

---

### Post by alexfish on 2012-09-04
also check "Devhelp"

with reference to this command,

"gdk_draw_drawable,"

some of the commands may be depreciated

regards

alexfish

---

### Post by Hetepeperfan on 2012-09-04
[http://developer.gnome.org/gdk/stable/gdk-Drawing-Primitives.html#gdk-draw-drawable](http://developer.gnome.org/gdk/stable/gdk-Drawing-Primitives.html#gdk-draw-drawable)

On the site above you can find that your function is deprecated, but it also shows you how you can work around your problem in a more up to date way.

cheers

---

### Post by Hairy_Palms on 2012-09-05
thanks, gonna try doing that, though i assumed deprecated meant still works just not recommended for new code, since its not new code but code im moving from gtk2

---

