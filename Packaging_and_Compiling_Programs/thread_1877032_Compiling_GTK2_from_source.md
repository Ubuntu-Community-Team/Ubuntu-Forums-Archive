---
title: "Compiling GTK2 from source"
date: 2011-11-07
forum: Packaging and Compiling Programs
---

### Post by eren.tantekin on 2011-11-07
[FONT=Arial][SIZE=2]I downloaded the source code for GTK2:


                                [FONT=Courier New]sudo apt-get build-dep libgtk2.0-0[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Courier New]
sudo apt-get source libgtk2.0-0
cd gtk+2.0-2.24.6/[/FONT]



After making the necessary changes, what should I do to compile and overwrite the GTK currently being used by Ubuntu?[/SIZE][/FONT]

---

### Post by SevenMachines on 2011-11-07
If you're sure you want to and know what you're doing
```
 $ debuild -b -us -uc
```
would build it

---

### Post by SevenMachines on 2011-11-07
It's important to note that you shouldn't use sudo with apt-get source, it doesn't need it. You might want to think about using the quilt patching system to make the changes too if you aren't already doing so. Finally, always remember to do (if you aren't already:) )
```
 $ dch -i
```
to insert a new changelog entry before debuilding

---

