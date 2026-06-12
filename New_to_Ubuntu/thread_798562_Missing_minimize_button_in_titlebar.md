---
title: "Missing minimize button in titlebar"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by DSdragondude on 2008-05-18
I have recently upgraded to Hardy Heron, and a problem that existed in gutsy has been carried over to this.

I am not using a desktop effect manager like compiz and I have found that the minimize button has gone missing !

Screenshot:
[[img]http://i40.servimg.com/u/f40/11/50/38/77/th/screen12.jpg[/img]](http://www.servimg.com/image_preview.php?i=143&u=11503877)


Can somebody help me?

---

### Post by benpage26 on 2008-05-18
Possibly a theme problem.

Go to System>Preferences>Appearance and choose the Human theme.

This may return your minimise button, (it may also reset your desktop background)

---

### Post by N.N. on 2008-05-18
If that fails, open a terminal and type the following command to revert the button layout of metacity to the default configuration: ```
gconftool --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"
```

---

