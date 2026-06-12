---
title: "kiba-dock physics"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-05-05
ok i installed the kiba dock(spent hours doing it)and no i dont no if i have to enable the physics or if they should be there or what...could someone please help me!!!

---

### Post by Grishka on 2008-05-05
> **betterthanjordan79 said:**
> ok i installed the kiba dock(spent hours doing it)and no i dont no if i have to enable the physics or if they should be there or what...could someone please help me!!!

physics engine is broken in the current kiba dock version. if you want jumping icons, you'll have to use an older version.

---

### Post by betterthanjordan79 on 2008-05-05
hahah u serious:lolflag: i spent so long gettin this 1 2 work haha!!any advide on how 2 install an older version wit physics in it??also wen i hover over the dock nd i have-say for example firefox on-firefox jumps about the screen...if ya dont understand me i could screen shot it for ya...its like the docks stuck always on top nd taken ova the bottem half of my screen.

---

### Post by Joeb454 on 2008-05-05
I was never a big fan of the physics - good from a technical point of view, but I found it pretty impractical from a usage point of view

---

### Post by betterthanjordan79 on 2008-05-05
yh i no its kinda pointless but it looks great...anyone know were i could get an older version with the workin physics??

---

### Post by Yoshiman007 on 2008-05-05
This thread should help you out. (Post #3 has the debs attached).

[http://ubuntuforums.org/showthread.php?t=728231&highlight=Kiba+dock+physics](http://ubuntuforums.org/showthread.php?t=728231&highlight=Kiba+dock+physics)

---

### Post by Grishka on 2008-05-05
> **betterthanjordan79 said:**
> yh i no its kinda pointless but it looks great...anyone know were i could get an older version with the workin physics??

here ya go.

---

### Post by betterthanjordan79 on 2008-05-06
>  Re: kiba-dock physics
Quote:
Originally Posted by betterthanjordan79 View Post
yh i no its kinda pointless but it looks great...anyone know were i could get an older version with the workin physics??
here ya go.
Attached Files
File Type: deb 	kiba-dock_0.1-1.2_i386.deb (105.2 KB, 3 views)

man i tried using this but i cant cus it tell me i have a newer version installed...

---

### Post by Grishka on 2008-05-06
> **betterthanjordan79 said:**
> man i tried using this but i cant cus it tell me i have a newer version installed...

if you do have a newer version installed, well, remove it. if not, I think the configuration files format changed a lot since then, so you'll have to remove kiba-dock configuration files before it'll work. try looking for a hidden folders called .kiba or .kiba-dock in your home directory, the ~/.config/ and ~/.gconf/apps/ folders.

---

