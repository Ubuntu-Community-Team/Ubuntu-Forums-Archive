---
title: "flash stopped working"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by Patricrawley on 2012-02-27
last night everything was fine. I log in this morning and do the system updates now i get this for every single flash video

---

### Post by ajgreeny on 2012-02-27
How was flash installed?  What version of flash have you got on the system?

Can you run ```
locate /libflashplayer.so
``` which will show if you have more than one version installed in different places, which can cause problems..

If you use firefox, in fact even if you don't use it, it is worth using the **flash-aid** add-on  as it overcomes many flash problems, and the installation for firefox in that manner will also allow chromium to use the exact same flash plugin.

---

### Post by Patricrawley on 2012-02-27
nothing was shown when i executed that command. so it seems it somehow got uninstalled

---

### Post by Patricrawley on 2012-02-27
```
patrick@Madeye:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
adobe-flashplugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
patrick@Madeye:~$ locate /libflashplayer.so

```
see my issue?

---

### Post by ajgreeny on 2012-02-27
OK, now is definitely the time to use flash-aid add-on for firefox.  It will, or should, search out and remove any strange or corrupt flash plugins that are causing problems and then install the version you ask it to install.  Use the wizard mode of running flash-aid as it gives more flexibility.

It is just possible that the beta plugin offered by flash-aid will not work with your system;  it will certainly not work in mine, so I set the flash-aid add-on to install the stable version from the repos.  If the beta will not work in your system, use the add-on a second time and install the stable as I have to do.

---

### Post by Patricrawley on 2012-02-27
i tried both of them, the locate command still returns nothing and the videos remain unwatchable

---

### Post by ajgreeny on 2012-02-28
Very odd!
Did the terminal that opens when running flash-aid show any error messages of any kind before telling you to close the terminal and restart firefox?

---

### Post by Gremlinzzz on 2012-02-28
Go into show hidden files and find .macromedia folder inside is a flash folder delete that and try to install flash player again.

---

