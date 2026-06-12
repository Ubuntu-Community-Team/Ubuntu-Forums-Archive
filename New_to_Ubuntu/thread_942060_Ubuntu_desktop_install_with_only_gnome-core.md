---
title: "Ubuntu desktop install with only gnome-core"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Ikith on 2008-10-08
Is there a way to install ubuntu desktop with only the gnome core or do I have to go get server and install gdm and gnome-core?

---

### Post by louieb on 2008-10-08
If I remember right you can do a command line only install from the desktop CD.  Don't know of anything that will automatically install just the Gnome core.  [HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")

---

### Post by Ikith on 2008-10-09
Would doing a:
sudo apt-get remove ubuntu-desktop
sudo apt-get remove gnome-desktop-environment

Get rid of gnome then I can do a:
sudo apt-get install gnome-core

Would this work or no go? I'm about to try it either way I have nothing to lose as everything is backed up.

---

### Post by jken146 on 2008-10-09
There is a minimal install CD [here]("https://help.ubuntu.com/community/Installation/MinimalCD") that lets you install only the really core Ubuntu packages if you like, then you have a command-line only system from which you can install only what you want.  This is the way I'd go about it.

---

### Post by metafa on 2012-07-11
> **Ikith said:**
> Would doing a:
sudo apt-get remove ubuntu-desktop
sudo apt-get remove gnome-desktop-environment

Get rid of gnome then I can do a:
sudo apt-get install gnome-core

Would this work or no go? I'm about to try it either way I have nothing to lose as everything is backed up.

did that work? I am very interested in doing the same. Thanks!

---

