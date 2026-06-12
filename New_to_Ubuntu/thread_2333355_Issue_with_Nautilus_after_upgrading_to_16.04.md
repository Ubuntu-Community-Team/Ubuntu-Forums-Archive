---
title: "Issue with Nautilus after upgrading to 16.04"
date: 2016-08-09
forum: New to Ubuntu
---

### Post by peacesells560 on 2016-08-09
Hi everyone, I have begun to have an issue with Nautilus after upgrading to 16.04. If I use Nautilus to access my external hard drive, maximise another window, and try to return to Nautilus by clicking on its icon, the little flag thing that indicates that there is an instance of a program running will disappear and it will open another Nautilus window instead of returning to the original window. This only occurs if I am accessing files on my external hard drive, if I access files on the internal hard drive, this does not occur.


Is there a way of fixing this?

---

### Post by tsjswimmer on 2016-08-14
This sounds like a Nautilus bug. You should file a bug report [here]("https://bugs.launchpad.net/"). Until the bug gets fixed, you should try accessing your external drive with another file manager. I like Thunar (sudo aptinstall thunar) and pcmanfm (sudo apt install pcmanfm), both which can be installed alongside Nautilus. Or, you can completely replace Nautilus with Nemo, which IMHO is as good of a file browser as anyone could ask for. See [here]("http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html") to learn how to install a version of Nemo, which has been modified to work better with Gnome and/or Unity.

---

### Post by mc4man on 2016-08-15
> **peacesells560 said:**
> If I use Nautilus to access my external hard drive, maximise another window, and try to return to Nautilus by clicking on its icon, the little flag thing that indicates that there is an instance of a program running will disappear and it will open another Nautilus window instead of returning to the original window.
If the "original window" means the window of the external drive then that's expected. External drives are now handled exclusively by the external drive icon, not the nautilus (Files) one.

---

