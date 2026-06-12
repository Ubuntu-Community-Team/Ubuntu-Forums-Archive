---
title: "Firefox extremely slow"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-04-22
I run Chrome, Chromium, and FireFox concurrently in 12.04 (Gnome 2 no effects) with 16 GB RAM

Over the past couple of weeks, FF has become increasingly and agonizingly slow, while the two C's are as blazing fast as ever. In FF, a search, or clicking a link takes 10-20 seconds or more to refresh the screen and typing is delayed appearing in a text box.

Anybody else having a problem with FF, or can shed any light on this?

Thanks.

---

### Post by Christmas on 2014-04-22
This may be related to add-ons or plug-ins that take up memory. Try running Firefox in safe mode, or disable all the add-ons and see if the problem persists. To run it in safe mode, from the terminal use **firefox -safe-mode**. The fact that Chrome works well means that it's a Firefox-specific issue. Also, try to create a new, empty profile and see if that helps (e.g. **firefox -P**).

---

### Post by Odyssey1942 on 2014-04-22
Did that. FF now lightnin' fast again.

How do I see a list of add-ons and extensions?

Thanks.

---

### Post by Christmas on 2014-04-22
You can go to the menu in the top-left side of the window and click on Add-ons, or use **Ctrl+Shift+A**, or if you have the menu enabled it should be under the Tools menu, or your best bet is to open a new tab and type **about:addons** in the address bar. You can enable/disable or remove whatever add-ons you like there (although just disable them one at a time and experiment).

---

