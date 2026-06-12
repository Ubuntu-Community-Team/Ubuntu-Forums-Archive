---
title: "How to close windows from overview"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by bobzxr on 2012-07-07
I do not know if this has already been asked, but how could I close any window from the overview, like in plain Gnome 3?

(like when you have more than 1 window from an application, you click on the apps icon on the left and you can see all windows from it - but you must click on a window and then close it.)

---

### Post by Kopkins on 2012-07-07
You should be able to use compiz to set a mouse button to close the windows. 

Install ccsm (compiz config settings manager)

```
sudo apt-get install compizconfig-settings-manager
```

Then open the launcher, type ccsm and press enter.

In the top left of ccsm type 'scale' into the filter box. Under the utility heading select 'Scale Add-ons.'

Make sure that this plugin is enabled, then select close window window for the mouse and choose whichever button you would like to use to close the window. Mouse button 1 is left click, button 2 is middle click (the scrollwheel click on normal mice), and button 3 is right click. You should be able to tap the top right corner of your trackpad as middle click if you have a laptop.

Kopkins

---

