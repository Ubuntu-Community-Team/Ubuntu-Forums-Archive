---
title: "Window options are hidden in Hardware sensor indicators"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2011-09-05
Hello,

The boxes to check to show temperature is blocked. Please see the screen shot.

Thanks.

---

### Post by lucazade on 2011-09-05
> **donniezazen said:**
> Hello,

The boxes to check to show temperature is blocked. Please see the screen shot.

Thanks.

it seems that the [GtkTreeView]("http://developer.gnome.org/gtk3/3.1/GtkTreeView.html") widget is quite buggy
the same behaviour is visible also in dconf-editor.

this should be fixed upstream in gtk3, probably a bug report is already opened.

---

### Post by donniezazen on 2011-09-05
> **lucazade said:**
> it seems that the [GtkTreeView]("http://developer.gnome.org/gtk3/3.1/GtkTreeView.html") widget is quite buggy
the same behaviour is visible also in dconf-editor.

this should be fixed upstream in gtk3, probably a bug report is already opened.

Thanks for the information.

---

### Post by mc4man on 2011-09-05
Don't have that hardware sensor deal but do see the same?? in dconf in some sections - the nautilus pref's is one where it occurs alot of the time
In that case (screen 1), if the entries are scrollable and there is one or more that's 'clickable', (screen 2) then by clicking on it the full section gets revealed
Certainly hope there is a bug & fix at some point

---

