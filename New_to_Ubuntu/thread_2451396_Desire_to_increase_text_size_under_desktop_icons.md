---
title: "Desire to increase text size under desktop icons"
date: 2020-10-03
forum: New to Ubuntu
---

### Post by bob-htz on 2020-10-03
I recently upgraded from Ubuntu 18.04 to 20.04. I use the Gnome desktop. I believe in 18.04, Gnome Tweaks tool would increase the font size of text under desktop icons. That does not appear to be the case for 20.04. I already have Large Text selected. I have eyesight issues. 

Is there a css file somewhere that I can edit to achieve this?

There other issue is associated with the Tweaks tool. I have the scaling factor set to greater than 1. Every time I restart, the scaling factor is ignored and I have to nudge the value to get the system to recognize it. I researched this and it does appear to be a software bug. 

Will there be a fix? Is there a work around (other than switching to another desktop)?

---

### Post by Dennis N on 2020-10-03
Using Ubuntu 20.04, with gnome-shell theme Flat-Remix-Dark.

You can increase text under desktop icons, but not independently - text size on the top bar, top bar menus, and desktop notifications will also increase. Edit the file **gnome-shell.css** which will be inside your gnome-shell theme folder, which may be a sub-folder of your applications theme folder, and change font size in this section:

```
/* Global Values */
stage {
  font-size: 10pt;
  color: #eeeeec; }

```

To prove it works, below are before and after screenshots when increasing font-size from 10pt to 13pt. Notice the panel width also increased to accommodate the larger font.

---

