---
title: "Desktop Wallpaper program"
date: 2007-01-05
forum: Programming Talk
---

### Post by SadaraX on 2007-01-05
I am thinking of trying to write my own Desktop Wallpaper program. How is the desktop wallpaper controlled within KDE? Is there an API for setting the wallpaper on the desktop(s)? Also, is there a more general method for setting the background, something that is control my the X-Session (I am using Xorg)?

I am thinking of trying to write my own Desktop Wallpaper program. I have several features in mind for it. Currently I have not found a good wallpaper program that does most of them. I hope this is the right forum.

One other thing, is there a way to know what a screen saver is active on a desktop? I am sure I could perform some hack using the 'ps' command and grepping the output, but I am looking for a better solution. Thanks in advance.

---

### Post by [woodstock] on 2007-01-05
You could try to actually write your program with wxwidget so that both Gnome and KDE user coud profit from it.
I can't actually contribute something useful for KDE but you could take a look at [wallpapoz]("http://wallpapoz.akbarhome.com/"). I don't like the approach of wallpapoz (i.e. it's GUI) but  there you can see how it is done for Gnome (and in Python). Maybe there is something similar for KDE and hopefully this give you some keywords for your further search.

---

