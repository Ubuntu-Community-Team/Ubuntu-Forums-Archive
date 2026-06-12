---
title: "Was it a good decision?"
date: 2009-12-17
forum: Programming Talk
---

### Post by kahumba on 2009-12-17
I think it was during the 100 papercuts when people asked to remove icons where they seemed redundant - but it seems Canonical over-engineered this by removing them in too many (random) cases.
Have a look at the right-click menu, there's no more an icon for "Document", "Spreadsheet" etc.
So now when programming I'm running into the following issue: in some cases the components despite being constructed with "from_stock" don't show up the icon (but according to sys prefs they should), in other cases - they do.
Is it only me thinking that by "solving" that papercut Canonical introduced other problem(s)?

---

### Post by kahumba on 2009-12-17
It looks like it's just me.

---

### Post by OrangeCrate on 2009-12-17
Go to System > Appearance > Interface, and put a check in the box for "Show Icons in Menus". If I understood your question correctly, that should do it for you...

(They turned off the icons by default in Karmic.)

---

### Post by kahumba on 2009-12-17
Oh boy that is embarrassing, thanks a lot!

---

### Post by OrangeCrate on 2009-12-17
> **kahumba said:**
> Oh boy that is embarrassing, **thanks a lot!**

You're welcome.

:)

---

### Post by Can+~ on 2009-12-17
Also, while tweaking my gnome configuration (gconf-editor), I stumbled with:

```
/desktop/gnome/interface/toolbar_icons_size
```

and set it to "small-toolbar"

I'm a bit disappointed that the appearance manager in ubuntu doesn't have a check box for that option, I was always annoyed by the size of the toolbar icons in nautilus.

---

