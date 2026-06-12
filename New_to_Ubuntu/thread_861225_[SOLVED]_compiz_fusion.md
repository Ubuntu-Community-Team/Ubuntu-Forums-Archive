---
title: "[SOLVED] compiz fusion"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by arkark07 on 2008-07-16
Have trolled through a fair bit of these forums and the CF forums and can't actually seem to find the information on how to install compiz fusion.   Am I missing something and being stupid?

Would like to know how to get CF up and running.
Have using v8.04

---

### Post by Troll_the_Great on 2008-07-16
Open Synaptic from System-Administration-Synaptic package manager and type "Compiz" an click search.Pick it up from the list,right click, mark for installation and you're done.
Then open a terminal from Application-Accessories-Terminal and type
```
sudo apt-get install compizconfig-settings-manager
```
Go to System-Preferences-Advance Desktop Effects Settings and configure it from there.
Cheers!

---

### Post by tuxxy on 2008-07-16
System > Preferences > Appearance

---

### Post by dracayr on 2008-07-16
compiz is installed by default. to be able to customize it, just install compizconfig-settings-manager and simple-compizconfig-settings-manager:

```
sudo apt-get install compizconfig-settings-manager simple-ccsm
```You can then customize using System&#8594;Preferences&#8594;Advanced Desktop effects settings. Also, you have to set Desktop effects to user defined in System&#8594;Preferences&#8594;Appearance

dracayr

---

### Post by arkark07 on 2008-07-16
Thanks guys, thats where I was getting stuck I saw it was installed but didn't know why I couldn't find the options etc. 
Got it working now. 
Now to figure out how to use it....

---

### Post by dracayr on 2008-07-16
@Troll: since hardy, you also need simple-ccsm, not only ccsm (at least I did)

dracayr

---

### Post by philinux on 2008-07-16
I only have compizconfig-settings-manager installed.

I have full compiz running without simple-ccsm being installed.

---

### Post by tuxxy on 2008-07-16
me aswell phil ;)

---

### Post by dracayr on 2008-07-16
?? strange I had only ccsm installed in Gutsy, but then I updated to hardy, and the option "user defined" in System&#8594;Preferences&#8594;Appearance was gone. I googled it and read that I had to install simple-ccsm. And it worked

dracayr

---

### Post by edwin2105z on 2008-07-16
sudo apt-get install compizconfig-settings-manager simple-ccsm     I typed in this code but it tells me. E: Couldn't find package compizconfig-settings-manager   what am i doing wrong?

---

