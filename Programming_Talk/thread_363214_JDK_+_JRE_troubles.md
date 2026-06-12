---
title: "JDK + JRE troubles"
date: 2007-02-16
forum: Programming Talk
---

### Post by r4ndom on 2007-02-16
I am currently running "breezy badger" and a'm having trouble it appears that ubuntu comes with jre 4.2 pre-installed well i install JDK 5.0 with JRE 5.0 included via synaptic and at first I would get version errors in firefox but I installed the plugin and now it is o.k however when i try to run any of my apps that include swing components i get the version error as ubuntu is trying to run it on 4.2 so in short how do I uninstall 4,2 it does not appear in synaptic although i think it is possible for me to update the symbolic link instead if so can you tell me what command to use as i am something of a nub. thanks

---

### Post by phossal on 2007-02-16
You might want to run:
```
sudo update-alternatives --config java
```
Select the proper version. Admittedly, I don't run Breezy, so I'm not 100% sure that line is the correct invocation.

---

### Post by r4ndom on 2007-02-17
wow thanks! sorry for the slow reply i could not get back to the forums because I was lagging.

---

