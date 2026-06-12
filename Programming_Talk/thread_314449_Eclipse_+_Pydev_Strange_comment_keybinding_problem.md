---
title: "Eclipse + Pydev Strange comment keybinding problem"
date: 2006-12-07
forum: Programming Talk
---

### Post by alanfranz on 2006-12-07
Hello, I'm using Eclipse 3.2 with Ubuntu Edgy. 
 
Eclipse SDK 
 
Version: 3.2.1 
Build id: M20060921-0945 (Ubuntu version: 3.2.1-0ubuntu1) 
 
 
I experienced the strange problem I describe belows, so I tried a full-reinstall of eclipse and all libraries; the problem persists even with a brand new install and a brand new workspace. 
 
the system is fully updated. Eclipse SDK and libraries are those that come with Ubuntu, while pydev 1.2.5 + pydev extensions were installed from the official repository (i never installed the pydev provided by ubuntu to prevent conflicts). The only addition is Lunar Editor Enhancements, but I've verified the issue arises even removing it. 
 
I can't tell exactly when/what happened, it was yesterday or today... I'm not able to to bind Ctrl+3 as Python Comment! 
 
If I try (beside the fact that a kind of blueish triangle appears at the left of the scope in Preferences -> Keys -> Modify, but I think it means something like 'User defined'). 
 
I tried removing all bindings for Ctrl+3 after taking a look at Keys->View (it was assigned to Python Comment only, BTW) and then setting it again to "Python Comment" in "Pydev editor" scope. 
 
Nothing happens! If I try using it, it's just like the selected text blinks and nothing more. 
 
After trying for a while, I removed the ctrl+2 keybinding (something for 'offline scripting' or similar) and assigned it to Python Comment; works 100%. 
 
Then I tried using Ctrl+3 (no keybinding is defined! in keys->view I simply see nothing under ctrl+3)... and it works a Python Uncomment, which is bound to Shift+Ctrl+3 instead (but shift+ctrl+3 works as well). 
 
I work with an external usb keyboard on a laptop, so I thought there might be something weird with it, I don't know, some strange keycode emitted, so I went back to the internal keyboard, I tried saving & rebooting everything, and the behaviour stays the same. 
 
Today Ubuntu released a lot of updates regarding gtk/glib and other important gui-related libraries... I don't know whatever other change has happened to my system. I'm posting this to the ubuntu forums as well... I tried looking for any enabled assistive technology, but it doesn't seem the case: if I press ctrl+downarrow I don't get the shift+ctrl+downarrow functionality. 
 
Has anybody experienced a similar problem and/or may know how to solve this?

---

