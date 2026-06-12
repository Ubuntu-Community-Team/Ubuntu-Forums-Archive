---
title: "Wine help"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-08-29
So i have installed a few games using Wine. Starcraft and WarCraft3. starcraft launches fine, but when i start WC3 the screen goes black, like its loading, but nothing ever happens. It doesnt lock up the computer, i can still use different workspaces, but that one workspace is just black.

Anyone had this problem before? or would know how to fix it?

---

### Post by anjilslaire on 2008-08-29
Make sure it's set to openGL. Check the wine subforums.

---

### Post by Codemastadink on 2008-08-29
> **anjilslaire said:**
> Make sure it's set to openGL. Check the wine subforums.

how do i make sure its set to openGL?

---

### Post by SunnyRabbiera on 2008-08-29
> **Codemastadink said:**
> how do i make sure its set to openGL?

well as he said check the wine subforum:
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

I know these games are known to work fairly well under wine.

---

### Post by circlemaster on 2008-08-29
You should follow the installation guides that the Wine AppDB gives you for this application: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=897](http://appdb.winehq.org/objectManager.php?sClass=application&iId=897)

Short answer to enable OpenGL in Warcraft 3: Open "regedit" and create a DWORD key named "Gfx OpenGL" in "HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III", set the value to 1.

---

### Post by sidewinder46 on 2008-08-29
> **Codemastadink said:**
> how do i make sure its set to openGL?

The way to run opengl with out changing settings is```
wine <program> -opengl
```

Try this 1st before changing the settings, if this solves your problem then change.

---

### Post by sidewinder46 on 2008-08-29
> **Codemastadink said:**
> how do i make sure its set to openGL?

The way to run opengpl with out changing settings is```
wine <program> -opengl
```

Try this 1st before changing the settings, if this solves your problem then change.wine warcraft --opengl command

---

