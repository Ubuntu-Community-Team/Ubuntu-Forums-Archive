---
title: "[SOLVED] PyGTK+ Problem"
date: 2008-05-28
forum: Programming Talk
---

### Post by ricegf on 2008-05-28
I'm having a PyGTK+ problem. I'd like to transfer a graphics file (say, a JPG or PNG) from disk to the clipboard in Python. The obvious way seems to be:

        pixbuf = gtk.gdk.pixbuf_new_from_file(tempfile)
        gtk.Clipboard.set_image(pixbuf)

However, this gives the following exception:

    gtk.Clipboard.set_image(pixbuf)
TypeError: descriptor 'set_image' requires a 'gtk.Clipboard' object but received a 'gtk.gdk.Pixbuf'

But the documentation for gtk.Clipboard.set_image claims it accepts a pixbuf - which certainly makes more sense than a Clipboard object! Here's the documentation:

gtk.Clipboard.set_image

    def set_image(pixbuf)

pixbuf :
        a gtk.gdk.Pixbuf.

What am I missing here?  Is this a bug in the set_image implementation, documentation, or programmer? :-)

I'm using Ubuntu 8.04 x86 32-bit with the default Python 2.5.2, running "python ./test.py" from the command line.

---

### Post by geirha on 2008-05-28
It typically means you should run that method on an instance of gtk.Clipboard and not the class itself. Try
```

clipboard= gtk.Clipboard()
clipboard.set_image(pixbuf)

```

---

### Post by ricegf on 2008-05-29
Yes, that's the problem.  As I suspected - programmer bug.  :-)

---

