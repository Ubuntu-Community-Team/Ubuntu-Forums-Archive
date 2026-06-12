---
title: "Google earth"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by telltommy on 2008-10-29
I installed it from the synaptic package mgr, but i can't find it to launch it. I know it's early but i think i'm losing it.

---

### Post by btermeli on 2008-10-29
terminal;

> dpkg -L google-earth

and you can make a button or shortcut.

---

### Post by SunnyRabbiera on 2008-10-29
yeh some stuff doesnt create menu entries.

---

### Post by vanadium101 on 2008-10-29
Should be in the menu under Applications->Internet->Google Earth

if it's not there try 'Alt + F2' and enter googleearth to see if it's installed 

If it is installed and not in the menu you will need to add it by right clicking on the menu and selecting Edit Menu and navigate to where it should be and adding a New Item. The command is googleearth

---

### Post by telltommy on 2008-10-29
terminal states no such application installed. I went back and selected reinstall from the synaptic package mgr, pasted commands in terminal and again "not found" weird.

---

### Post by stephanvaningen on 2008-10-29
Sometimes it takes a while before it appears in the menu (something to do with caching of the menu items or something?)

How you can double-check: right-click on the menu option 'Application', select Edit Menu, there select Internet and see if Google Earth is checked

---

### Post by eternalnewbee on 2008-10-29
After reading this Thread I went to Synaptic and installed Google. After having finished the installation, I went to Main Menu > Internet, and voila. There it was.

---

### Post by sdowney717 on 2008-10-29
you can also download googleearth .bin file from google directly.
make it executable by going to properties
then from a terminal in the directory run it "./filename.bin"

For some reason google earth in synaotic for ibex would not install.

you can also edit the menu and add the icon

---

### Post by telltommy on 2008-10-29
tom@tom-desktop:~$ dpkg -L google-earth 
Package `google-earth' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
tom@tom-desktop:~$ 


still not on my computer. Again, I downloaded from synaptic package mgr, selected apply, all is normal but where did it go?

---

### Post by vanadium101 on 2008-10-29
have you tried my instructions above? 

also you may need to take the '-' out of the googleearth

eg:
```
dpkg -L googleearth
```

---

### Post by telltommy on 2008-10-29
tried all instructions and so far it's not installed.

---

### Post by earthpigg on 2008-10-29
tried reinstalling it via synaptic?

---

### Post by telltommy on 2008-10-29
I uninstalled then reinstalled but still it doesn't show. Also tried a reboot, just incase

---

### Post by kiwi-pete on 2008-12-12
Can I but in here. I have had googleearth running on my  ibex for a day. Now it loads and shows stars.
I cannot do anything else with it as all other commands seemed to be greyed out.
Nothing in places or layers either.

---

### Post by pgdave on 2008-12-15
> **kiwi-pete said:**
> Can I but in here. I have had googleearth running on my  ibex for a day. Now it loads and shows stars.
I cannot do anything else with it as all other commands seemed to be greyed out.
Nothing in places or layers either.
That's what I had with the previous version(4.2). Have you loaded the latest GE version? Mine's version 4.3beta, dated 8 Jul 2008, and works fine.

---

