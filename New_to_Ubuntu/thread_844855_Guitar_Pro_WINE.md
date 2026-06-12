---
title: "Guitar Pro WINE"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by MasterCylinder on 2008-06-30
So I start gp5.exe with Wine... everything is kosher until I load a file... There is only staff with blank spots where the notes/tab would be.

---

### Post by RomeReactor on 2008-06-30
Hi. Please open a terminal (Applications->Accessories->Terminal) and paste this:
```
wine ~/.wine/drive_c/Program\ Files/Guitar\ Pro\ 5/GP5.exe
```
Then press ENTER; next, load a file and if the problem happens again, post the output left in the terminal.

---

### Post by MasterCylinder on 2008-06-30
wine: cannot find '/home/mcmanus/.wine/drive_c/Program Files/Guitar Pro 5/GP5.exe'

I have to go to the mounted volume on my desktop 52.4gb (where my XP installation is) and browse to find Guitar Pro

---

### Post by RequinB4 on 2008-06-30
Here is the appDB page for this program [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3782](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3782)

Follow the instructions and messages there -- always check the appdb when trying to get a wine application to work.

---

### Post by RomeReactor on 2008-06-30
> **MasterCylinder said:**
> wine: cannot find '/home/mcmanus/.wine/drive_c/Program Files/Guitar Pro 5/GP5.exe'

I have to go to the mounted volume on my desktop 52.4gb (where my XP installation is) and browse to find Guitar Pro

In the terminal write:
```
wine 
```
Note: That's **wine** with one space in front of it. Then open nautilus, navigate to where the GP5.exe file is, and drag it to the terminal, then press ENTER.

---

### Post by whitethorn on 2008-06-30
Have you tried Tuxguitar?  Isn't as feature rich as GP5 but it works for me.

---

