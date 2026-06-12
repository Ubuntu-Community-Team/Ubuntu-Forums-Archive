---
title: "GLADE Unresponsive"
date: 2010-08-26
forum: Programming Talk
---

### Post by xaegis on 2010-08-26
Programming question:
I am running Python 2.6 and Glade 3.6.7
So I am attempting to use glade to develop a GUI but whenever I run any libglade ".glade" code then nothing happens.
```

import gtk.glade


class DoomWindowGUI:
    def __init__(self):
        self.window = gtk.glade.XML('doomviewer.glade','window1')


if __name__=='__main__':
    DoomWindowGUI
    gtk.main()


```

Am I doing something wrong?
it just seems to freeze as if waiting for something.If I write the files out in Tk or wxGlade they are fine and everything runs. Is libglade depreciated or something? Also, how do/should I use GTKBuilder instead of glade? How is it different? (every time I try to save a file in GTKBuilder format it doesn't run. the error I get is:

```
libglade WARNING**: Expected <glade-interface>.Got<interface>
```

What does it mean???
:D
Thanks everyone!

-e

---

### Post by xaegis on 2010-08-27
ok the behavior is as if there is no:

```
self.window.show()
```

in the XML file if that helps...
;)

---

### Post by oldfred on 2010-08-27
Glade writes in either libglade or builder. Builder is supposedly the newer way to do things:

builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)
py faqs builder
[http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp](http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp)

---

### Post by xaegis on 2010-08-27
Yes, I can't get libglade files to work so now I'm trying GTKbuilder.

Thank you!

-e

---

### Post by alexfish on 2010-08-27
hi

you could have a look at quickly it will do most of the above Glade , python , builder
once the project is created , then import gtk

[https://wiki.ubuntu.com/Quickly](https://wiki.ubuntu.com/Quickly)

regards

alexfish

---

### Post by oldfred on 2010-08-27
I did not remember my first like was that old micahcarrick as now you do not have to the the convert. The latest glade saves directly to the builder format.
```

    def __init__(self):
        try:
            self.builder = gtk.Builder()
            self.builder.add_from_file("testimport.glade")
        except:
            self.show_error_dlg("Failed to load UI XML file: testimport.glade")
            sys.exit(1)

        # get the widgets which will be referenced in callbacks
        self.window = self.builder.get_object("window1")
        self.notebook1 = self.builder.get_object("notebook1")
        self.statusbar = self.builder.get_object("statusbar1")


```

---

### Post by xaegis on 2010-08-29
I'm using Quickly now and its really awesome. Cant wait till its a bit more mature and polished. :) and it is based on GTKBuilder.

problem solved.

thanks everyone!

-e

---

