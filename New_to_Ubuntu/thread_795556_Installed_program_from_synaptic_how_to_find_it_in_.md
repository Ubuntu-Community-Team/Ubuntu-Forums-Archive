---
title: "Installed program from synaptic how to find it in Menu?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by markotitel on 2008-05-15
Hi,

Ive installed Gisomount, I start it from console but with SUDO ( dont know why ), and I cant find it in applications. How can I find out whether some program will place it in menu or not ?

---

### Post by nowshining on 2008-05-15
u can either try logging out or back in or if it didn't create a menu for u - u'll have to manually create one. :)

---

### Post by z.solstice on 2008-05-15
You can try System>Preferences>Control Center and then click on "Main Menu"
This brings up the selection of what you want to display on your menus...Make sure it is checked...hope this helps

---

### Post by markotitel on 2008-05-15
thx, I have to make entry in menu manually for this program.

---

### Post by balagosa on 2008-05-15
Gisomount?? or GMount-Iso??

because i also have GMount-Iso installed and it is under Applications->System Tools->(here)

or you can make a launcher. Type in what name you want, and in the command type in "Gmount-iso"

---

### Post by Lektorvis on 2008-05-19
gISOMount will only run as root, this means you have to start it from the terminal.
It's still possible to make an entry from the launcher I selected "Program in Terminal"  and typed "sudo gISOMount" to the command line.
Plz correct me if there is an easier way to run this app.

---

### Post by nowshining on 2008-05-20
u can also use gksu in front of it to get the GUI password prompt which should help with ur having to run in terminal, it's up to u, and it's roughly the same. :)

---

