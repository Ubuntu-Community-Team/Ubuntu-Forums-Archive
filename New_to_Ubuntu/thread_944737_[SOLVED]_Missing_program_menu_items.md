---
title: "[SOLVED] Missing program menu items"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by thgthg on 2008-10-11
The drop down program menu does not work any more. Places and system works as normal. What can I do to restore menu function to normal?

---

### Post by roger_1960 on 2008-10-11
Hi

Right click anywhere on the top panel

Select "add to panel"

select "main menu"

click on add

---

### Post by thgthg on 2008-10-12
OK, thats fine, but now I can not edit the content in the menu. The system trying to start menu edit but nothing happens.

---

### Post by thgthg on 2008-10-12
Hi again,
one more thing I have to add, both upper and lower menu bars is missing,

---

### Post by thane1 on 2008-10-12
Right click on the Ubuntu Logo icon at the very top left of screen, then select Edit Menus.  Click on the option on left and add check marks in the right hand pane for any desired applications, which are unchecked.  See if this works.  Cheers.

---

### Post by thgthg on 2008-10-12
Tnx  thane1, but as long as I can't start "edit menus" it's hard to add any aplications. If I try to start "Edit menus" the "wait" symbol show up for 10 to 15 secs but nothing more happens. The menu bars, upper and lower, is there but invisible. I can start "places" and "system", but not program menu.

---

### Post by thane1 on 2008-10-12
Just a guess here (maybe someone else could comment on this)... I'm wondering if searching for and selecting "gnome-menus" in Synaptic and marking for reinstallation, followed by  doing the reinstall might solve your problem.  Cheers.

---

### Post by bumanie on 2008-10-12
Why not try reinstalling ubuntu desktop - it should reinstall anything that is missing or messed up. In terminal > sudo aptitude install ubuntu-desktop

---

### Post by thgthg on 2008-10-12
OK, I tried to reinstall desktop in terminal. Now the both bars is OK, but still, the Program Menu is impossible to open and I can't run "MainMenu".

---

### Post by mc4man on 2008-10-12
If your Applications menu is non functional then go to home folder -> .config -> menus and delete the file 'applications.menu'. Exit out and your Applications menu will be restored.  (.config is a 'hidden' file, enable under view

---

### Post by thgthg on 2008-10-12
Great, now everything works just fine. Case closed
Thank you.

---

