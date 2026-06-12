---
title: "adding a run command shortcut to the dock"
date: 2020-05-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-05-15
running 20.04. alt + f2 brings up the run command. i want to put a shortcut on my dock. there is a way to do this but i forgot /tks

---

### Post by pantazi on 2020-05-15
[http://ubuntuhandbook.org/index.php/2019/04/pin-application-shortcuts-desktop-ubuntu-19-04/](http://ubuntuhandbook.org/index.php/2019/04/pin-application-shortcuts-desktop-ubuntu-19-04/)

---

### Post by rburkartjo on 2020-05-15
i just want to add the run command shortcut not a particular shortcut.

---

### Post by rburkartjo on 2020-05-15
also use to be called run application

---

### Post by pantazi on 2020-05-15
Ah yes, apologies. (note to self: read twice!)

---

### Post by ActionParsnip on 2020-05-15
The way I used to do it is make a script in /usr/bin then make a ".desktop" file in /usr/share/applications to run the script. You can then pin the item to the side bar as you expect. I then divorced myself from all that and just run the script with ALT + F2 in gmrun (I use OpenBox as standalone WM)

---

### Post by rburkartjo on 2020-05-15
act tks that did the trick

---

