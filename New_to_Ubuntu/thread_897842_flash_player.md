---
title: "flash player"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-22
i have the plugins of both adobe flash player 9 and 10(tools>addons>plugins).now,i want to totally obliterate them from my system,how can i do that?

---

### Post by stonecoldjha on 2008-08-22
the screenshot clarifies this

---

### Post by Gannon8 on 2008-08-22
Depending on what flash player you installed and how you installed it, it may be as simple as uninstalling a package to removing system files. But why would you want to anyway?

---

### Post by stonecoldjha on 2008-08-22
because i want to begin afresh and install flash player 10.how can i get that done?

---

### Post by stonecoldjha on 2008-08-22
how can i totally efface flash player and everything related

---

### Post by Majorix on 2008-08-22
Run Synaptic and type in "flash player" for the search term. That would most likely show Flash 9.0. You can remove that using Synaptic and you will be left with Flash 10 to work with.

---

### Post by Cheesehead on 2008-08-22
Proper uninstall depends on exactly how you installed...

If you installed using Add/Remove or Synaptic or Firefox-Plug-In...then you uninstall the same way.

If you compiled (make) the file, then you unmake it the same way.

If you installed a .tar file using a script or instructions off the web, then go back and undo all those instructions.

If you want details on how to uninstall a firefox plugin, then tell us exactly how you installed it, each step in order.

---

### Post by AnonCat on 2008-08-22
delete any libflashplayer.so files in the following directories and replace them with the newest flashplayer .so file after deleting libflashsupport.  

sudo apt-get remove -y --purge libflashsupport  

/home/.mozilla 

and/or  

/usr/lib/firefox(your-version-number)/plugins

---

