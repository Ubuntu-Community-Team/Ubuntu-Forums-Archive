---
title: "What's the actual size of a given GtkIconSize?"
date: 2009-12-10
forum: Programming Talk
---

### Post by froggyswamp on 2009-12-10
In my menu I have items with images from stock and created by myself. My problem is for my images in the menu items to be of same size as those which are created from stock, otherwise in same menu I end up having smaller and bigger images in menu items.
I thought I'd use the value/size of GtkIconSize "GTK_ICON_SIZE_MENU" to resize my images:
```

typedef enum
{
  GTK_ICON_SIZE_INVALID,
  GTK_ICON_SIZE_MENU,
  GTK_ICON_SIZE_SMALL_TOOLBAR,
  GTK_ICON_SIZE_LARGE_TOOLBAR,
  GTK_ICON_SIZE_BUTTON,
  GTK_ICON_SIZE_DND,
  GTK_ICON_SIZE_DIALOG
} GtkIconSize;

```
but it turns out it's not an actual size, it's an id. Any suggestions?

---

