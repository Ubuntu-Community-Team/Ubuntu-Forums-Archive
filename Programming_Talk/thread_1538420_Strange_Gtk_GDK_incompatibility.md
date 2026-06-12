---
title: "Strange Gtk GDK incompatibility"
date: 2010-07-25
forum: Programming Talk
---

### Post by TheHimself on 2010-07-25
I'm writing a program using Gtk and C. When I use the function

```
gtk_image_set_from_file (GTK_IMAGE(image),current_file.path);

```
I get the desired result but when I use

```
   
pixbuf=gdk_pixbuf_new_from_file  ( current_file.path,    &err);
gtk_image_set_from_pixbuf   (GTK_IMAGE(image),   pixbuf);

```

the function gdk_pixbuf_new_from_file returns a NULL pointer and when I add
```
printf("%s\n",err->message);
```
I get a segmentation fault. I have no idea what's going on.:confused:

---

### Post by TheHimself on 2010-07-25
I found out! the error pointer must be set to NULL when declaired.

```
GError *err=NULL;
```

Kind of stupid.

---

