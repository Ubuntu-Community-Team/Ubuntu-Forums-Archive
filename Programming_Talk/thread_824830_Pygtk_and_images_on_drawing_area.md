---
title: "Pygtk and images on drawing area"
date: 2008-06-10
forum: Programming Talk
---

### Post by christooss on 2008-06-10
Hi,

I'm having problems putting images on drawing area. I would like to have image present on drawing area at start of program. Than I would scribble something on it.

```
image = gtk.Image()
image.set_from_file("apple-red.png")
image.show()
# a button to contain the image widget
button = gtk.Button()
button.add(image)
button.show()
```

This code is from pygtk tutorial and it puts image on button with button.add but drawing area doesn't have that option.

I found this
[http://www.pygtk.org/pygtk2tutorial/ch-DrawingArea.html](http://www.pygtk.org/pygtk2tutorial/ch-DrawingArea.html)

but I'm getting problems from GC part.

I think I have to add image like this: ```
drawable.draw_image(gc, image, xsrc, ysrc, xdest, ydest, width, height)

``` but I get this error

```
AttributeError: 'gtk.DrawingArea' object has no attribute 'draw_image'
```

Any ideas

---

