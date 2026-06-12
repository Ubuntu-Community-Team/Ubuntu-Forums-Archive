---
title: "Python and Glade"
date: 2009-12-18
forum: Programming Talk
---

### Post by AndThenWhat on 2009-12-18
Hello,

So I'm new to Python and Glade development.  I have got a basic Python program to show my Glade file, however two of my buttons on the Glade file are Stock buttons and they are not showing the default Gnome images on them, they are only showing the button's text.  Is this a bug?

---

### Post by Can+~ on 2009-12-19
The gnome team decided to "hide" the icons in the buttons, along with the menu icons. A decision that I didn't like, at all.

If you want them back:

```
gconf-editor /desktop/gnome/interface/buttons_have_icons
```

And set it to "true". And for the menu icons, there's an option in the appearance menu for that one, or look for it in the gconf-editor.

---

