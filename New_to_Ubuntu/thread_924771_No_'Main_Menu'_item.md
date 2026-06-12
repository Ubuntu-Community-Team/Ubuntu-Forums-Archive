---
title: "No 'Main Menu' item"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by WVSteelers28 on 2008-09-19
Hi all (Once again.  I'm learning :) ).

After fixing my issue of not having anything on my desktop when I boot up (No panels, etc.) I noticed that the 'Main Menu' link item has disappeared from my Preferences list under System.  

I've searched through Add/Remove programs and Synaptic Package Manager to see if it wasn't installed, but couldn't find anything that would relate to it.  Any suggestions?

Thanks,
WVSteelers28

---

### Post by k33bz on 2008-09-19
right click on your panel, go to add to panel, you will find it there

---

### Post by nkri on 2008-09-19
If you can't add it using k33bz's method, you could install alacarte, the menu editor, if it isn't installed, or reinstall if it's broken.

```
sudo apt-get install alacarte
```

Good luck!
-nkri

---

### Post by WVSteelers28 on 2008-09-19
While that was fast, but thanks both nkri your solution work.

---

### Post by washeddang on 2008-09-19
And if that doesn't work, try:
-Right-click anywhere on your menu.
-Click Edit Menus. This will open the Main Menu window.
-Click on Preferences under System on the left panel
-Make sure Main Menu on the right panel is checked

---

### Post by lswb on 2008-09-19
Open a terminal or press Alt-F2 and type 

alacarte

and the menu editor will open. Then you can add it back to system/preferences.

---

