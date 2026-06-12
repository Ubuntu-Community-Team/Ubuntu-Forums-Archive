---
title: "cairo dock logoff"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by dadsbrkn on 2008-05-01
I installed the latest version of cairo dock on my recent hardy upgrade,it is working fine except the logoff icon does not work on the dock.  How do I configure this to bring up the gnome logoff screen?

---

### Post by dadsbrkn on 2008-05-22
I'm still unable to figure this out, but I have a new problem.When I mouse over the autohide area to lanch the dock, it launches, but does not render the dock and I can only see a thin line where the top of the dock should be. Can anybody help?:(

---

### Post by dadsbrkn on 2008-06-08
Well my other 2 problems are solved by an upgrade to the latest version, but now I am unable to change themes.  Any ideas??????:confused:

---

### Post by spiderbatdad on 2008-06-08
How did you install the dock? Did you get the deb packages, including the plugins? Did you install the dependencies not met in those packages? And are you running xcompmgr or compiz....?

---

### Post by dadsbrkn on 2008-06-08
Well I originally downloaded the packages from get-deb (I believe), and had a mostly functioning system until the upgrade using the built in check for updates.  I am using xcomp and everything was pretty much working before the upgrade.  Now my previous problems are answered and this one is new.  I can change the view from 2-d to3-d, but when I try to change the theme it stays the same.  Thanks

---

### Post by spiderbatdad on 2008-06-08
Maybe try this: ```
sudo killall cairo-dock
```
Make sure xcompmgr is running. I use ALT+F2 for that. Then launch cairo-dock from the terminal to see if you have any errors.

Once it is all running, you can add it and xcompmgr to sessions, to enable it at startup.


Get the two debs here:[https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14108](https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14108)
for v 1.5.6

---

### Post by dadsbrkn on 2008-06-08
Well it's working now,thanks for your help.

---

