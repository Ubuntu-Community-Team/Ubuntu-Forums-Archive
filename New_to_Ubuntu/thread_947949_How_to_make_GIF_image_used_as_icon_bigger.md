---
title: "How to make GIF image used as icon bigger?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-14
Hello Fellow Ubunteros!

I created a GIF file of a photo I like so that I can use it as an icon for a folder I created.

Question: How can I make the icon a bit BIGGER? It's appearing too small.

Thank you

---

### Post by eolson on 2008-10-14
Right click on the icon and select open with Gimp
When Gimp opens,  Right click on it again
Select Image Scale
from there you can resize it in whatever units you want, pixels, inches, etc.

Save as
and your done.

If you still don't like the size, just do it over.   Just use save as instead of save and you will always have your original.

---

### Post by suomalainen on 2008-10-14
Thanks Eolson..... Everything you say works to the "T" but it doesn't help make the icon bigger... This is really strange....

---

### Post by drs305 on 2008-10-14
> **suomalainen said:**
> Thanks Eolson..... Everything you say works to the "T" but it doesn't help make the icon bigger... This is really strange....

Metacity controls the size of *all* icons in both Nautilus and on the Desktop. So if you want to make all icons larger, but not just one, you can open gconf-editor:
```
gconf-editor /apps/nautilus/icon_view/default_zoom_level
```
The values are smallest, smaller, small, standard, large, larger, largest.

Two below zoom level is a setting to change thumbnail sizes.

Again, this will change all icon images.

---

