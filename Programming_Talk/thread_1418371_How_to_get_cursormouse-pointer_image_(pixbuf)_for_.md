---
title: "How to get cursor/mouse-pointer image (pixbuf) for an application window."
date: 2010-02-28
forum: Programming Talk
---

### Post by moma on 2010-02-28
Hello,

I would like to get the image of cursor/mouse-pointer for an  arbitrary application window in Linux - using Python libraries.

I have studied several libraries that support Python, but haven't found a suitable function to read cursor or mouse-pointer image.

**PyGTK:**[http://www.pygtk.org/docs/pygtk/index.html]("http://www.pygtk.org/docs/pygtk/index.html")  No success.
**Wnck python library: **[http://library.gnome.org/devel/libwnck/stable/index.html]("http://library.gnome.org/devel/libwnck/stable/index.html")  No success.
**Xlib Python:**[http://python-xlib.sourceforge.net/doc/html/index.html]("http://python-xlib.sourceforge.net/doc/html/index.html") Did not find any suitable function. Did I miss something?

I've done it in c-code earlier and it works well. It uses XFixesGetCursorImage(display) function.

The c-code is here: [http://code.google.com/p/gscreendump/source/browse/trunk/src/sd_xutils.c](http://code.google.com/p/gscreendump/source/browse/trunk/src/sd_xutils.c)

[PHP]GdkPixbuf *get_cursor_pixbuf(Display *display, GdkWindow *gdk_win, gint *cursor_x,gint *cursor_y, gint *offset_x , gint *offset_y/*x-y hot spot */) {

        GdkWindow *gdk_root = gdk_get_default_root_window();

        /* Cursor image */
        GdkPixbuf *cursor_pixbuf = NULL;

        /* Check if the XFIXES extension is present */
        int event, error;
        if (XFixesQueryExtension(display, &event, &error))
        {
                XFixesCursorImage *cur = XFixesGetCursorImage(display);

                *cursor_x = cur->x;
                *cursor_y = cur->x;
                *offset_x = cur->xhot;
                *offset_y = cur->yhot;
....
[/PHP]

I would like to use a Python library on Linux.
Can you help?

My system is: Ubuntu 9.10 64bit.
http:/www.futuredesktop.org (.com)

Kindly
  Moma
  Grønland

---

### Post by moma on 2010-03-01
Hello,

Ok, this case is now solved.
I was informed about the Python's ctypes module. Ctypes is used to call external functions from Python. So I can call libXfixes.so library and its XFixesGetCursorImage() function from Python.

For more info, read this thread.
[http://www.daa.com.au/pipermail/pygtk/2010-March/018337.html](http://www.daa.com.au/pipermail/pygtk/2010-March/018337.html)
Includes also an example.

You will also need x.py and xlib.py from [http://code.google.com/p/pyxlib-ctypes/](http://code.google.com/p/pyxlib-ctypes/)
---

GTK/GDK should absolutely have a function to get pixbuf of current mouse or cursor.
Why on earth getting cursor image is so f* difficult in GTK and Unix/Linux???

---

