---
title: "how do you make scrollbar wider?"
date: 2020-09-03
forum: New to Ubuntu
---

### Post by pgau6016-16acc on 2020-09-03
i have carpal tunnel syndrome and it is extremely difficult and painful trying to use this skinny scrollbar.  is there a away to make it wider if NOT someone please tell me and i'll just delete ubuntu studio and go back to mint 19.3


so frustrated 

trying to read what seems like millions of posts and no help on my problem connecting my drum set (dm10 mkii pro) and the scroll just makes it more painful

---

### Post by Holger_Gehrke on 2020-09-03
The easy solution is to select a different theme in the appearance settings applet (should be in the menu, otherwise 'xfce4-appearance-settings' from the command line). Both the 'Raleigh' and the 'High Contrast' theme have wider scrollbars. There are probably other themes you can install that also have this feature.

The advanced solution would be to create a file '~/.config/gtk-3.0/gtk.css' and have your own CSS to change width of vertical and height of horizontal scrollbars. Alternatively you could change the CSS in the gtk.css file of the theme you use.

Holger

---

### Post by pgau6016-16acc on 2020-09-03
ok thanks, will do so as soon as i learn what a CSS is and how to create or edit one is.

---

### Post by Holger_Gehrke on 2020-09-04
CSS means Cascading Style Sheets and is the language used on the web to set up the appearance of web-pages. GTK 3 uses CSS to set up the appearance of the elements of the user interface. A CSS file contains rules which are made up of selectors - these select what elements are to be styled - and property settings - those change a specific aspect of the appearance. Obviously the CSS used by GTK has a lot of element names for use in selectors which are not found in CSS for web pages and there are some properties which are not implemented. You'd end up with something like: '.scrollbar.vertical { width:50px }' or '.scrollbar { -GtkRange-slider-width:20 }' (neither of these are tested, I just looked at '/usr/share/themes/Radiance/gtk-3.0/gtk-widgets.css to find the selectors and properties which should influence the scrollbars).

Holger

---

