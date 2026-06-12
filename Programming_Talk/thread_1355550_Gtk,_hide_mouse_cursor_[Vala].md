---
title: "Gtk, hide mouse cursor [Vala]"
date: 2009-12-15
forum: Programming Talk
---

### Post by kumoshk on 2009-12-15
So, I've been trying to figure out how to hide the mouse cursor in a Gtk program (in Vala), or how to make it invisible.

Anyway, I found some vague references to the objects needed, as well as this code:
```
var pix_data = "#define invisible_cursor_width 1\n#define invisible_cursor_height 1\n#define invisible_cursor_x_hot 0\n#define invisible_cursor_y_hot 0\nstatic unsigned short invisible_cursor_bits[] = {\n0x0000 };";
// this.window refers to a Gdk.Window, which is available after show_all is called
var pix = Gdk.Pixmap.create_from_data(this.window, pix_data, 1, 1, 1, col_black, col_black);
this.window.set_cursor(new Cursor.from_pixmap(pix, pix, col_black, col_black, 0, 0));
```

However, the code doesn't work for me, even after switching out col_black for a real color object (empty), and specifying Gdk.Cursor instead of just Cursor. It compiles and all, but it doesn't work. Can anyone show me a working example of code adapted from this?

Here are the runtime errors I get:
(myProgram:32103): Gdk-CRITICAL **: _gdk_drawable_get_source_drawable: assertion `GDK_IS_DRAWABLE (drawable)' failed
(myProgram:32103): Gdk-CRITICAL **: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed

The keyword 'this' in my program code refers to a Gtk.Window object.

---

### Post by ebbe on 2012-02-17
If anyone is looking for the answer, this is what worked for me:
```

Gdk.Color col_black;
Gdk.Color.parse("fff", out col_black);
var pix = new Gdk.Pixmap(null, 1, 1, 1);
element_covering_entire_application.window.cursor = new Gdk.Cursor.from_pixmap(pix, pix, col_black, col_black, 0, 0);

```

*element_covering_entire_application* is in my application a HBox covering the entire application.

---

