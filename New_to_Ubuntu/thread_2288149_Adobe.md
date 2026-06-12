---
title: "Adobe"
date: 2015-07-24
forum: New to Ubuntu
---

### Post by Ian_Morral on 2015-07-24
Hi, I'm a newbe and having trouble downloading Adobe reader, I've downloaded the file but cannot find how to run it so I can view 'You Tube' and 'Facebook' vids. Any suggestions?

---

### Post by Frogs Hair on 2015-07-24
Hello and Welcome 

Do you mean Adobe flash or reader ? If you you need flash for video look for the adobe flash plugin installer in the software center. I don't use reader which is a windows only application AFIK.

---

### Post by SeijiSensei on 2015-07-24
There are better PDF readers available here than Adobe Reader.  Try evince on Unity/GNOME systems, or okular on KDE.  

Firefox now comes with a built-in PDF viewer.

If you're talking about watching YouTube, then you are looking for FlashPlayer.

---

### Post by Vladlenin5000 on 2015-07-24
> **SeijiSensei said:**
> If you're talking about watching YouTube, then you are looking for FlashPlayer.

Indeed, but currently not even that is needed because the default for Youtube and all major streaming services is HTML5. Don't know about Facebook, don' t use it, don' t care...

---

### Post by SeijiSensei on 2015-07-24
Most commercial services don't support HTML5 video because they need to impose DRM.

---

### Post by Vladlenin5000 on 2015-07-24
> **SeijiSensei said:**
> Most commercial services don't support HTML5 video because they need to impose DRM.

True but not applicable (again, eventually applicable to Facebooks vids - don't know, don't care - or others but not Youtube, Vimeo, DailyMotion, etc...).
If DRM is enforced then I'm afraid you won't be able to access that contents from Linux, even with Chrome with the latest Flash, unless you put in place some (or many) workarounds. That's why I avoid anything with it (DRM).

---

### Post by Julind on 2015-07-24
He is surely talking about adobe flash player since he mentioned videos.
> **Ian_Morral said:**
> ... so I can view 'You Tube' and 'Facebook' vids. Any suggestions?
[HR][/HR]Ian, to **install the flash plugin** required to play videos open a terminal using the **Ctrl+Alt+T** key combination and in the terminal **paste** this
 ```
sudo apt-get update && sudo apt-get install adobe-flashplugin
```
and hit **enter**. It will ask for your password, and follow the on screen instructions, until its complete.

If you find the terminal installation tricky or it doesn't work, refer to this tutorial link below (You can skip to step 3 if you see that Canonical Partners is checked)
[https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash](https://wiki.ubuntu.com/Chromium/Getting-Partner-Flash)

---

