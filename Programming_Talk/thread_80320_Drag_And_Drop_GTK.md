---
title: "Drag And Drop GTK"
date: 2005-10-21
forum: Programming Talk
---

### Post by josuealcalde on 2005-10-21
Well, I am developing a LibGlade application using c++ and gtk.

I have been able to do it, but my application has some areas which are textview widgets.
Something similar to this: [https://developer.berlios.de/dbimage.php?id=1801](https://developer.berlios.de/dbimage.php?id=1801)

I do something like this:

```
gtk_drag_dest_set (window_main,			   
			   GTK_DEST_DEFAULT_ALL,
			   drag_types, n_drag_types,  GDK_ACTION_COPY);
```

But dnd does't work over the textviews, only in the rest of the window.
Do you know how could I correct this?

---

