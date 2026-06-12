---
title: "When I open up my Desktop apps..the windows have no close or minimise options"
date: 2014-06-23
forum: New to Ubuntu
---

### Post by Louise_Avon on 2014-06-23
When i open up system settings or any of my desktop apps...i can no longer move my windows around the screen. There is no toolbar options with the 'x' to close window, or to minimise the window. This is making it difficult for me to operate or use the computer. I think some keyboard shortcut has been pressed by mistake. How do I get my window toolbars back? Firefox is the only one which remains intact.:(

---

### Post by JeQhdMD on 2014-06-23
Have you changed the default Ubuntu theme in any way?  Did you install and use the "unity tweak" tool (or any  other similar software like Gnome teak tool)?  Did you add new software (like nemo file manager) or anything else before seeing the altered windows settings?

---

### Post by deadflowr on 2014-06-24
Seems like window decoration is turned off.:(

Try this
open a terminal and install compizconfig-settings-manager
If you can launch a terminal from the menu, good. If not press ctrl+alt+T.
```
sudo apt-get install compizconfig-settings-manager
```
(if it is already installed, ignore and go to step two)
Now, again, if you can open the program you installed through the menu good, if not, then run simply
```
ccsm
```
When you first launch it, you'll get a warning about being careful, so be careful.
Once it is open go to the section Effects, and see whether or not Window Decoration is checked.
If it is not checked, check it.
See this helps.

---

### Post by Louise_Avon on 2014-06-26
Thankyou&#8230;this worked.

---

### Post by LastDino on 2014-06-26
Good, I'm glad. Please mark the thread as solved from thread tools above.

---

