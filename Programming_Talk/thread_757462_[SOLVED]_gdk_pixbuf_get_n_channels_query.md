---
title: "[SOLVED] gdk_pixbuf_get_n_channels query"
date: 2008-04-16
forum: Programming Talk
---

### Post by dosh on 2008-04-16
I am having problems with the gdk_pixbuf_get_n_channels command
I have the following code inside a program
 ```

GdkPixbuf *img;
int c;
......
img=gdk_pixbuf_new_from_file("test.png");
......
c=gdk_pixbuf_get_n_channels(img);
......

```

the result value of c comes out to be less than 0. I am very confused by the result as obviously I can't have a negative number of channels.

---

### Post by WW on 2008-04-17
It is probably an error code.  You should check that gk_pixbuf_new_from_file succeeded before calling gdk_pixbuf_get_n_channel(img).

By the way, according to [this page](http://library.gnome.org/devel/gdk-pixbuf/stable/gdk-pixbuf-file-loading.html), gdk_pixbuf_new_from_file takes two arguments.

---

### Post by dosh on 2008-04-17
Thanks WW

Yes a typo on mine it should read 
img=gdk_pixbuf_new_from_file("test.png",err);
I actullay pulled the loading of the file bit of code straight from a previous working program I had. I think you are right though I will see if the "err" part of the code brings up any info that might help me.

---

### Post by dosh on 2008-04-17
worked out the error
the problem was in the err being incorrectly referenced should be as below
```
GdkPixbuf *img;
int c;
GError *err     \* this was GError **err *\
......
img=gdk_pixbuf_new_from_file("test.png",&err);   \* NOT (...,err) *\
......
c=gdk_pixbuf_get_n_channels(img);
......
```

---

