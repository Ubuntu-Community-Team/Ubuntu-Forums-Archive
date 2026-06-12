---
title: "reinstalled chrome"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by ramtin2000b on 2012-03-27
I  uninstalled using the Software Center, but the minute I reinstalled  Google CHrome, the extensions and everything were still there... How do I  remove this Thanks.

---

### Post by raja.genupula on 2012-03-27
you have to a purge uninstall to remove all its things completely . 
do this in your terminal 
```
sudo apt-get remove --purge <name of the app >
```

---

### Post by Elfy on 2012-03-27
apt-get or synaptic or software centre will only remove the installed packages

to completely remove things like extensions you need to find the folder in your home

I don't use chrome but firefox for instance has a folder in /home/user called .mozilla 

folders with name preceded by . are hidden - ctrl+h to see them in nautilus

---

