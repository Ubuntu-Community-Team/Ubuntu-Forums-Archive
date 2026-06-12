---
title: "[SOLVED] More disappearing programs"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-15
I downloaded more programs from Synaptic but they didn't show up anywhere on my Applications. When I typed the package name in Terminal, they "launched into GUI form" (I really have no idea how to describe it). Is this the only way to launch these programs?

---

### Post by InfinityCircuit on 2008-08-15
Which programs? GUIs should install a .desktop that will automatically add itself to your menu.  If they don't, go to Applications -> Right Click -> Edit Menus and see if the applications are there but just not checked.  If they aren't there, then make a new shortcut and create an icon/description for it.

---

### Post by t0p on 2008-08-15
> **zzzonked said:**
> I downloaded more programs from Synaptic but they didn't show up anywhere on my Applications. When I typed the package name in Terminal, they "launched into GUI form" (I really have no idea how to describe it). Is this the only way to launch these programs?

You can also launch programs by pressing **Alt+F2** and typing the name of the app you want to run.  But that's not much different from typing into a terminal, is it?

You can also add a **customized launcher** to a panel on your desktop.  To do this: right-click on the panel, select to Add New Item, select Customized Launcher, customize it to launch the app you want.

---

### Post by dannyboy79 on 2008-08-15
if they are gui apps, and they require sudo to run, make sure you run them using gksudo instead of sudo.

---

