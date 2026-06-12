---
title: "get button press events from a gtk image in C"
date: 2010-11-22
forum: Programming Talk
---

### Post by Woody1987 on 2010-11-22
I have a gtk button with an image which I want have flush with the background, i.e. no border around it. From what I can tell gtk does not have the functions available to do this. My solution to this is to use a gtk image which is flush with the background and enable button press events on it thus making it act like a button but look correct at the same time. How do I get this image to receive button press events?

Code thus far:
```

updateButtonIcon = gtk_image_new_from_stock(GTK_STOCK_REFRESH, GTK_ICON_SIZE_BUTTON);
gtk_box_pack_start(GTK_BOX(hboxTitle), updateButtonIcon, FALSE, FALSE, 10);

```

Attached are examples of the correct looking way (image) and the incorrect looking way (button).

---

### Post by StephenF on 2010-11-22
Try putting it in one of these.

[http://library.gnome.org/devel/gtk/2.21/GtkEventBox.html](http://library.gnome.org/devel/gtk/2.21/GtkEventBox.html)

---

