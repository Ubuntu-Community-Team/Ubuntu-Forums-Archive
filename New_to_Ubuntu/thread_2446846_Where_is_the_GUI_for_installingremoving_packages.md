---
title: "Where is the GUI for installing/removing packages"
date: 2020-07-07
forum: New to Ubuntu
---

### Post by zeekstern on 2020-07-07
I read where there is a GUI in Gnome that shows you all packages installed and allows you to easily uninstall them. 
 I did a new full install today (20.04) from CD and have an app called Software & Updates. This does not list the packages, but it does list 5 Categories like Canonical supported, Community maintained, Proprietary drivers etc. 

The other program is Software Updater and that isn't it either.
Anyone know what I am looking for:confused:

Thanks Zeek

---

### Post by tea for one on 2020-07-07
Fair chance that you are looking for synaptic, which is not included in the original installation.

```
sudo apt install synaptic
```

---

### Post by rbmorse on 2020-07-07
synaptic

For Ubuntu users it is available in repository and can be installed with the command:

sudo apt install synaptic

---

### Post by zeekstern on 2020-07-07
Thank you both Tea For One and rbmorse. I should have been able to guess that one. Geezz.

---

### Post by monkeybrain20122 on 2020-07-07
The default software store is gnome-software, it should be there by default. Synpatic offers more fine grain control so for example it contains libraries, dev packages and additional components that you won't find in the software store. But most casual users probably don't need to know these details so the software store provides a nice pretty gui interface.

---

