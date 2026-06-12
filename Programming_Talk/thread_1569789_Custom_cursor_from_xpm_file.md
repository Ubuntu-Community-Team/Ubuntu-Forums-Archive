---
title: "Custom cursor from xpm file"
date: 2010-09-07
forum: Programming Talk
---

### Post by bstree on 2010-09-07
Hi,

I want to use a custom cursor that I am loading from xpm file
how can I load an xpm file? 

thanks,

Ilan

---

### Post by lykeion on 2010-09-07
Have you tried open the xpm file with gimp?

To make a cursor in Ubuntu involves a little bit of fiddling around, see this:
[http://www.ehow.com/how_5026012_make-cursors-file-ubuntu.html](http://www.ehow.com/how_5026012_make-cursors-file-ubuntu.html)

---

### Post by bstree on 2010-09-07
thanks,

so now I need to create the cursor via pix buf?

---

### Post by bstree on 2010-09-07
finally I didn't use xpm
this is what I did

Glib::RefPtr<Gdk::Pixbuf> pixbuf;
pixbuf = Gdk::Pixbuf::create_from_file("gfx/32x32/pen.png");    get_window()->set_cursor(Gdk::Cursor(get_display(), pixbuf, 2,26));

my mistake was to use it on the constructor of the window
so I failed at get_display() because it returned null

---

