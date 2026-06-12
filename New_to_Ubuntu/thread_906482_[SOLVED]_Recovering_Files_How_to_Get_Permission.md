---
title: "[SOLVED] Recovering Files: How to Get Permission?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by E.T.Smith on 2008-08-31
After an attempted upgrade to 8.04 [that went very bad]("http://ubuntuforums.org/showthread.php?t=899064"), I'm trying a fresh install. Fortunately, all my old files are still intact and easily recoverable from the hard drive while running the live CD. Unfortunately, they also still have all their old permissions in place, so I can't recover the hidden files, such as my firefox profile (and Battle of Wesnoth progress, too). Is there a way for me to change the permissions or failing that somehow get the system to ignore them so they can be copied? Remember, I can't run from hard drive, it can only be read as media.

---

### Post by natirips on 2008-08-31
Sorry to violate your signature, but press ALT+F2 and type "gksudo nautilus" (without the quotes). Now you should be able to access all files. Be carefull though, sudo/gksudo nautilus gives you root/administrative rights over system, so it can be dangeours (if misused) since it can do wathever you tell it to do (including instantly delete all files on you computer at your wish/command).

---

### Post by E.T.Smith on 2008-08-31
Excellent. To avoid any dire errors, how do I turn off sudo when I'm done?

---

### Post by E.T.Smith on 2008-08-31
Scratch that, doesn't work. While the sudo command lets me view the hidden files through nautilus, I'm still stuck with a permission ban when I try to copy them.

---

### Post by natirips on 2008-08-31
> **E.T.Smith said:**
> Excellent. To avoid any dire errors, how do I turn off sudo when I'm done?
Just press the little X at the upper-right corner of the window.
> **E.T.Smith said:**
> Scratch that, doesn't work. While the sudo command lets me view the hidden files through nautilus, I'm still stuck with a permission ban when I try to copy them.
Open two or more* of such Nautilus windows and copy files between them. I suppose you had permission problems when trying to paste somewhere outside the "gksudo nautilus" window.

Edit:
*Either File->New Window or keep doing ALT+F2 thing again and again until you have desired number of windows.

---

### Post by E.T.Smith on 2008-09-03
That seems to have done it, thanks.

---

