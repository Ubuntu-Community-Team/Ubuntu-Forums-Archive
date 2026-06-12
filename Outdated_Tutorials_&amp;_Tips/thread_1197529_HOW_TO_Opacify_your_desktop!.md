---
title: "HOW TO: Opacify your desktop!"
date: 2009-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by keplerspeed on 2009-06-26
Four things to make your desktop look slick and transparent:

1) Transparent Taskbar:

This one is easy and well known. Just right click on a blank section of the taskbar, properties>background, select solid colour and desired opacity.

2) Transparent Terminal:

Also a well known easy one. Just open a terminal and go to edit>profilepreferences>background and select transparent.

3) Transparent windows borders:

I didnt know this was possible, but is quite easy. Open a terminal and enter:
```

gconf-editor

```
Next go to apps>gwd and edit:
```

metacity_theme_active_shade_opacity

```
and
```

metacity_theme_shade_opacity

```
To a value of around 0.3 (or anything from 0 to 1)

4) Transparent Gnome menus:

This was even easier! Go to system>preferences>compiz config settings manager (ensure you have it installed).

Enable "Opacity, brightness and saturation" by ticking it's box, and then click on it to enter it's configuration menu. Click the add "new" icon, and add these two items:
```

DropdownMenu

```
with a value of 90 or so, to make gnome menus transparent, and add:

```

popupmenu

```
with a value of 90 to make right click menus transparent.

---

### Post by Rim3nX on 2010-11-19
Thanks bro, helped a lot :)

---

### Post by tom957 on 2010-11-19
Very cool. Thanks!

---

### Post by Jechem on 2010-11-19
great tip. thanks. something new to be learned everyday with ubuntu

---

