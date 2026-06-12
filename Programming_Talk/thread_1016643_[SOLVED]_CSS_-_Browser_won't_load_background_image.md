---
title: "[SOLVED] CSS - Browser won't load background image"
date: 2008-12-20
forum: Programming Talk
---

### Post by Kinetic_lord on 2008-12-20
I am building a site and, i edited a few pictures to use as menu's, buttons, etc... The problem is, i have placed the background of the main header using: background-image: url('menu/bar_menu'); When i see the preview in Quanta plus, the background appears, but in Firefox, i can only see the buttons and a white background. This is the CSS:
```
#header {
	top: 0px;
	left: 0px;
	width: 800px;
	background-image: url('menu/bar_menu.png');
}

#left_menu {
	top: 250px;
	left: 0px;
	width: 250px;
	background-image: url('menu/bar_left.png');
}

#content {
	top: 250px;
	left: 250px;
}
```
So what is the problem? The Web Developers toolbar in Firefox shows no CSS errors.

---

### Post by Kinetic_lord on 2008-12-20
Found the problem! Thanks for the help! :)

---

### Post by TreeFinger on 2008-12-20
so what was the problem?

---

### Post by Kinetic_lord on 2008-12-22
I wrote: <link type="text/css" href="style.css" />

i should've wrote: <link type="text/css" **rel="stylesheet"** href="style.css">

---

