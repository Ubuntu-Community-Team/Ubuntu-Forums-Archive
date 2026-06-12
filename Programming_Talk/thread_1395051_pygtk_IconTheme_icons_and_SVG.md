---
title: "pygtk: IconTheme icons and SVG"
date: 2010-01-31
forum: Programming Talk
---

### Post by spillz on 2010-01-31
I wonder if someone can explain why I can't load SVG icons using the standard IconTheme/IconInfo methods... (I'm using Ubuntu Karmic (AMD 64) system.)

To illustrate, with pygtk installed, start python interpreter then:

```

import gtk
i = gtk.icon_theme_get_default()
ii = i.lookup_icon("drive-harddisk-usb",gtk.ICON_SIZE_MENU,0)

```

this should retrieve an IconInfo structure for the icon "drive-harddisk-usb". (Why "drive-harddisk-usb"? Because that's what the gio VolumeMonitor gives me)

```

print ii.get_filename()

```

prints '/usr/share/icons/Humanity/devices/16/drive-harddisk-usb.svg'

which looks sensible. but then 

```

pb = ii.load_icon()
print pb.get_height(),pb.get_width()

```

prints "1 1"

wtf? On another system (running Jaunty), I run the same code which points to a png instead of a svg and everything works as expected (i.e. I get a 16x16 pixbug.

Now if I run:

```

pb2=gtk.gdk.pixbuf_new_from_file(ii.get_filename())
print pb2.get_height(),pb2.get_width()

```

prints "16 16" as expected.

This seems like a bit of a hack, which makes me think there must be another (simpler) way to render the device icons returned from gio VolumeMonitor.

---

### Post by steveneddy on 2010-02-05
I'm having the issue of Intrepid not displaying svg icons.

Very frustrating.....

---

### Post by kahumba on 2010-02-05
An SVG afaik has a preferred size and perhaps Python doesn't honor it, try setting the preferred size before or after reading the SVG and see what happens.

---

