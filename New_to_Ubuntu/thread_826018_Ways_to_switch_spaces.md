---
title: "Ways to switch spaces?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by polotip on 2008-06-11
I was wondering If there was a cool way to switch spaces so that you could see it and stuff.  Ive seen some people do it online ,and was wondering how it is done.  Also, is there a way to have more than two workspaces open?
Brian

---

### Post by powerpleb on 2008-06-11
> **polotip said:**
> I was wondering If there was a cool way to switch spaces so that you could see it and stuff.  Ive seen some people do it online ,and was wondering how it is done.  Also, is there a way to have more than two workspaces open?
Brian

CTRL + ALT + Left/Right
or CTRL + ALT + Down

If you have compiz hold down CTRL + ALT and drag the mouse around with the Left button held down

---

### Post by Inxsible on 2008-06-11
if you have enabled compiz(provided it works on your machine) scrolling your mouse wheel on the desktop will switch spaces. It does that even if you dont have compiz, but you won't get the cube rotation.

---

### Post by aktiwers on 2008-06-11
To have more than 2 spaces rightclick on the workspace switcher and pick preferences. Then add more desktops.

Do you have effects enabled? Go to System =>Preferences => Appearance
And look under the "visual effects" tab.
Now enable them if you didn't already.

Then open op the terminal(Aplications =>Accessories => Terminal)
And install the compizconfig-settings manager like this:
```
sudo apt-get install compizconfig-settings-manager
```When its done type in:
```
ccsm
```In there you can add lots of effects to your desktop..  "Desktop wall" or "Desktop Cube" gives you some animation when changing desktop. You can play around in there and add stuff. By the the way, the shortcut to change desktop is CTRL+ALT+ &#8592; &#8594; (keyboard arrows) 

Good luck :)

---

