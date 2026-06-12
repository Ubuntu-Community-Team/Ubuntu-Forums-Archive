---
title: "Python+Gtk: Icon of a file/folder"
date: 2008-07-27
forum: Programming Talk
---

### Post by fas on 2008-07-27
Hello everyone

I need the corresponding icon as shown in the Nautilus File Manager for any given path, e.g. /home/username, /media/mounteddevice, /music_file.mp3, /textdocument.txt etc.

I am helpless since every file type has its specific system icon (pdf, mp3, ...). Up until now I have just used two icons: stock_folder and gtk-file:

```

theme = gtk.icon_theme_get_default()
folder = gtk.Image()
folder.set_from_pixbuf(theme.load_icon("stock_folder",24 , gtk.ICON_LOOKUP_FORCE_SVG))

```

Is there a way to get those file/folder-specific icons?
Is it maybe even possible to create thumbnail previews like Nautilus does?

Regards

---

