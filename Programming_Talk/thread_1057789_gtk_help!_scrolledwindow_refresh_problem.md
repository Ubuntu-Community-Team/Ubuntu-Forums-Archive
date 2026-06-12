---
title: "gtk help! scrolledwindow refresh problem"
date: 2009-02-02
forum: Programming Talk
---

### Post by mahajanudit on 2009-02-02
iam fairly new to gtk development in c language and i really want to dig in. iam creating an image viewer like picasaphotoviewer. now i have a gtkscrolledwindow and in that gtkimage as the viewport. now when i resize the image, i.e. zoom in or zoom out, how do i refresh the viewport or the whole scrolledwindow for that matter for the change to show. like in java there is repaint() function to repaint any changes made.
plz help

---

### Post by kknd on 2009-02-02
Maybe gtk_widget_queue_draw or gtk_widget_queue_resize?

---

