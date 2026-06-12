---
title: "[Gtk] How to get ICON_SIZE_MENU actual size?"
date: 2010-09-06
forum: Programming Talk
---

### Post by kahumba on 2010-09-06
Hi,
When creating an "image menu item" for a pop-up menu one usually creates its image (icon) by creating a Gtk::Image with 2 params: a stock id and ICON_SIZE_MENU as its size (which is just a constant/enum, it is not an actual size, but internally gtk somehow knows the size that corresponds to it).

In my case the image for the "image menu item" is in the default theme, not in the gtk stock, so I have to construct the Gtk::Image differently, through IconTheme::lookup_icon() where I have to specify the actual size of the image, not a constant like ICON_SIZE_MENU, but since I don't know what size corresponds to ICON_SIZE_MENU I have to guess it which is bad cause it might be different on others computers or might change on my own computer if I switch to a different theme some day.

Hopefully I made myself clear..

Any ideas how to get around this?

---

