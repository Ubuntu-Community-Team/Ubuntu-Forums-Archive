---
title: "Drag file onto program to load (Vala/GTK)"
date: 2009-12-01
forum: Programming Talk
---

### Post by kumoshk on 2009-12-01
I have the following code:
```
this.connect("drag_motion", this.motionDrag);
this.connect("drag_drop", this.dropDrag);
this.connect("drag_data_received", this.gotDrag);
```

It gives me the following run-time errors:
```
(reader:9573): GLib-GObject-WARNING **: IA__g_object_connect: invalid signal spec "Gdk.drag_motion"

(reader:9573): GLib-GObject-WARNING **: IA__g_object_connect: invalid signal spec "Gdk.drag_drop"

(reader:9573): GLib-GObject-WARNING **: IA__g_object_connect: invalid signal spec "Gdk.drag_data_received"
```

What are the real names for such as "drag_drop" in Vala? I got the names from Gtk in Python, but apparently they don't work. I couldn't find the Vala equivalents.

---

### Post by Vadi on 2009-12-01
Hm, it is there: [http://references.valadoc.org/gtk+-2.0/Gtk.Widget.drag_drop.html](http://references.valadoc.org/gtk+-2.0/Gtk.Widget.drag_drop.html)

Try using "drag-drop" as a name.

---

### Post by kumoshk on 2009-12-01
> **Vadi said:**
> Hm, it is there: [http://references.valadoc.org/gtk+-2.0/Gtk.Widget.drag_drop.html](http://references.valadoc.org/gtk+-2.0/Gtk.Widget.drag_drop.html)

Try using "drag-drop" as a name.

Using hyphens doesn't seem to work. I don't know why, but it has to be a string, too (so I don't think I can reference a widget to get the value). Is there another method that would work without a string there? Is there a way to find the exact value names it's looking for?

---

### Post by kumoshk on 2009-12-01
If there's another solution to what I want to do, feel free to let me know.

All I need to happen is have my program load a file (from Nautilus or whatever) if it's dragged into it (while open—it would be nice if I could get it to do it while not open, as well: as it stands it'll only do it from the command-line).

---

