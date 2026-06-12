---
title: "Configuring the terminal"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-23
In Kubuntu 7.10, you can configure the terminal (Konsole) to remember it's size and position. Since the Terminal in Ubuntu 7.10 seems to open in the same size and position everytime I launch it, is there a way to configure it like Kubuntu? Thanks.

---

### Post by NightwishFan on 2008-05-23
I am not sure. There might be an option for it in gconf. Well thats gnome fer ya. (it was a joke I like gnome)

---

### Post by anaconda on 2008-05-23
I dont know about remembering its position,

but you can define where and which size it opens by default by opening it with eg. command
```
gnome-terminal --geometry 120x40+180+150
```

the 120x40 is the size of it
and +180+150 defines the location.. I think the first number states how many pixels from the left and the second how many pixels from the top..

---

### Post by mlissner on 2008-05-23
I believe you can also handle this through compiz, in the ccsm options.

---

