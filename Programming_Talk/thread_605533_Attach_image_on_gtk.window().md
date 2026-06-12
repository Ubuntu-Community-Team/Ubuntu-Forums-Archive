---
title: "Attach image on gtk.window()"
date: 2007-11-07
forum: Programming Talk
---

### Post by tux-world on 2007-11-07
hi , In python (pygtk) , how can I create a popup window and attach a picture to it. I want to hide window's titlebar and borders. Actually, I want to show only the picture and nothing else.(without use xpm_data into source code):confused:

thanks. can you introducing sample?

---

### Post by Quikee on 2007-11-07
I think this is what you are looking for:

```

import gtk

window = gtk.Window()
window.set_decorated(False)

pix = gtk.gdk.pixbuf_new_from_file("test.png")
pixmap, mask = pix.render_pixmap_and_mask()

window.realize()

style = window.style
style.bg_pixmap[gtk.STATE_NORMAL] = pixmap
window.set_style(style)
window.resize(pix.get_width(), pix.get_height())

if mask:
	window.shape_combine_mask(mask, 0, 0)

window.show()
gtk.main()

```

---

### Post by tux-world on 2007-11-08
OH !! thanks , thats right!! thank you very much

---

