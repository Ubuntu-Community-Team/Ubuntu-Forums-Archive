---
title: "Cannot return default contents in the top toolbar :("
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Fabolous_Boy on 2008-11-06
:(:confused: how can i return the default settings for the top toolbar. i mean like with the "Applications" and "Settings" bar in the top with the Ubuntu Signbeside them. i deleted the top toolbar cuz i thought it might come back when i make a new one...

IM SO STUPID!!! How can i return the default TOP toolbar??? PLEASE HELP!!!

im using Intrepid Ibex by the way...Desktop version

---

### Post by sharkbite1414 on 2008-11-06
make a new toolbar
right click
add to toolbar
now select all the stuff you what on your toolbar

P.S.
Next time read the warning massages that pop up because you press delete:lolflag:

---

### Post by Fabolous_Boy on 2008-11-06
> **sharkbite1414 said:**
> make a new toolbar
right click
add to toolbar
now select all the stuff you what on your toolbar

P.S.
Next time read the warning massages that pop up because you press delete:lolflag:

I  dont thing you got what i meant.

OK, remember that from the first time you install  Ubuntu, theres the top toolbar complete with the "System", "Applications", The "Mozilla Firefox" icon and then the "Evolution Mail" icon on the left side;and at the right side, theres your name, The Update Manager, The Battery Life icon, the Internet Connection manager icon etc. etc....they are all shortcuts...and i want them all to come back...i want them to come back...like normalm...like from the start...

well what i did is that i accidentaly deleted a colon thing on the toolbar and then all the vital stuff for me got deleted from the toolbar and then i messed it up even more by deleting the whole toolbar...

HELP ME!!! PLEASE!!!

---

### Post by Yashiro on 2008-11-06
You could press Alt+F2 and type users-admin
This will let you create a new user.
Create a new user.
Set the profile as administrator in the third box.
Fill in the rest.

When done, log out. Log in as this new user.
You've lost some settings but your bars are back and all your apps are still on the machine.

---

### Post by m_duck on 2008-11-06
Or, open your home folder. Press control + H (or View -> Show Hidden Files) to show hidden files. Find the ".gconf" folder, and open it, then go into the "apps" folder. Find the folder in here called "panel". Either delete this folder or rename it (in case you want it restored in the future) to something like "panel.BAK". Log out and log back in again and the original default panels should be restored.

---

