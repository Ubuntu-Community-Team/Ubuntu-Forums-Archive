---
title: "removing default themes"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Roen hayden on 2008-06-05
how do i remove default themes? once i have one theme installed remove the rest and make that one default?

---

### Post by adobrakic on 2008-06-05
System > Preferences > Appearance

Delete button, to the left of Save As

---

### Post by Roen hayden on 2008-06-05
Nope the delete button is grayed out will not let me delete the ones that come with ubuntu.

---

### Post by erginemr on 2008-06-05
There are four packages regarding themes in Ubuntu:
gnome-themes, gnome-themes-extras, gnome-accessibility-themes & gnome-accessibility-themes-extras

You may consider reviewing their descriptions from Synaptic and remove the ones you don't need.

---

### Post by Roen hayden on 2008-06-05
i basically want to get rid of the human themes.

---

### Post by pmlxuser on 2008-06-05
> **Roen hayden said:**
> i basically want to get rid of the human themes.
basically all the theme files are in /usr/share/themes so if you run a 
$ sudo nautilus /user/share/themes
you will be able to delete any theme you want,
i have forgoten where the icons are installed at 
But removing a themes folder from this would definately delete the theme

---

### Post by erginemr on 2008-06-05
> **pmlxuser said:**
> basically all the theme files are in /usr/share/themes so if you run a 
$ sudo nautilus /user/share/themes
you will be able to delete any theme you want,
i have forgoten where the icons are installed at 
But removing a themes folder from this would definately delete the theme

Theme icons are located under "/usr/share/theme_name".

---

### Post by Roen hayden on 2008-06-05
Theme icons are located under "/usr/share/theme_name".

says that its not found

---

### Post by SunnyRabbiera on 2008-06-05
why do you want to get rid of the ubuntu human theme?
anyhow to delete at least its folder, you can try to delete the human folder in /usr/share/themes.

They were giving you an example up there, there is no such folder as "theme name" in that section.

---

