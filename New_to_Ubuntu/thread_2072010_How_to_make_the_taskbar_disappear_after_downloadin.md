---
title: "How to make the taskbar disappear after downloading Docky"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by agszepp on 2012-10-16
How would I make the task bar disappear? I have downloaded Docky, and I want that as my taskbar.

---

### Post by Jake Sweeney on 2012-11-03
Do you mean the unity bar at the side of the screen?
If so, then you can tweak the settings for it and it's behaviour by installing a program called MyUnity.

To install it run this command in the terminal:

sudo add-apt-repository ppa:myunity/ppa
sudo apt-get update
sudo apt-get install myunity

Then set the behaviour of the unity taskbar as "hidden" and it should go away. :)

---

### Post by newb85 on 2012-11-03
If you're talking about auto-hiding the Launcher, you don't need MyUnity to do that.  System Settings>Appearance>Behavior(tab)

---

### Post by philinux on 2012-11-03
> **newb85 said:**
> If you're talking about auto-hiding the Launcher, you don't need MyUnity to do that.  System Settings>Appearance>Behavior(tab)

+1 also there is no myunity currently for 12.10

> === The Official MyUnity PPA ===

This PPA contains backports for Ubuntu Stable Releases (11.04/Natty and 11.10/Oneiric). If you are using Precise (the current development release, which in time will become 12.04), please don't use this PPA: MyUnity is already availble from Ubuntu Archive through Ubuntu Software Center.


---

