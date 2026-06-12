---
title: "HOWTO: Moving buttons to the left like on a Mac"
date: 2008-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by kspncr on 2008-08-04
If you come from a Mac background and want to help ease the transition to Ubuntu, this might help if you keep going to the upper left hand corner to close a window, it's on the right in Ubuntu. At least by default;)

Or if you just want those buttons on the left because you think it's cool, then keep reading.

Okay, here goes:

1. Press alt+F2 and type "gconf-editor" and press enter.

2. Navigate through apps->metacity->general

3. In the box on the right, double click "button_layout"

4. Change the value from "menu:minimize,maximize,close" to "close,minimize,maximize:menu"

5. Hit Okay and you're done! Wasn't that easy?

6. If you ever want to change it back, it's as easy as changing "close,minimize,maximize:menu" back to "menu:minimize,maximize,close"

---

### Post by bengrout on 2008-08-06
Thank you, that was really useful.

---

### Post by raul_ on 2008-08-06
You can also do that with Emerald, if you're using compiz

---

### Post by chillyperson23 on 2010-11-11
Any way to do this in KDE 4.5?

---

