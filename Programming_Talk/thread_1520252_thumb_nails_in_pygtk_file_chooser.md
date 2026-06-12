---
title: "thumb nails in pygtk file chooser?"
date: 2010-06-29
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-06-29
In this code snippet for a pygtk file chooser, how to I set it to show thumb nail views?

```
dialog = gtk.FileChooserDialog("Open..",
                               None,
                               gtk.FILE_CHOOSER_ACTION_OPEN,
                               (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                                gtk.STOCK_OPEN, gtk.RESPONSE_OK))
dialog.set_default_response(gtk.RESPONSE_OK)

filter = gtk.FileFilter()
filter.set_name("All files")
filter.add_pattern("*")
dialog.add_filter(filter)

filter = gtk.FileFilter()
filter.set_name("Images")
filter.add_mime_type("image/png")
filter.add_mime_type("image/jpeg")
filter.add_mime_type("image/gif")
filter.add_pattern("*.png")
filter.add_pattern("*.jpg")
filter.add_pattern("*.gif")
filter.add_pattern("*.tif")
filter.add_pattern("*.xpm")
dialog.add_filter(filter)

response = dialog.run()
if response == gtk.RESPONSE_OK:
    print dialog.get_filename(), 'selected'
elif response == gtk.RESPONSE_CANCEL:
    print 'Closed, no files selected'
dialog.destroy()

```

---

### Post by OgreProgrammer on 2010-07-01
It seems that the current gtk+ does not feature this. Gimp and several other applications do things slightly different with a single preview window to the side.

---

