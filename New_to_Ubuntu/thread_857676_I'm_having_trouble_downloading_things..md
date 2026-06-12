---
title: "I'm having trouble downloading things."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by mightyjon on 2008-07-12
When I download something (limewire, java) I have to install it in order to run it. However, it says something like I can only run one software management tool at once. Unfortunately, I have no idea what else is running. So I've restarted my computer assuming that it would close me out of all programs. Its preventing me from downloading stuff.

When I go to Add/Remove to install third party programs that look nice and didn't come with Ubuntu, like AbiWord or Amarock, it says

 "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report."

---

### Post by appi2012 on 2008-07-12
were you installing updates when trying to install something?

---

### Post by NovruzeliH on 2008-07-12
if u are trying to install updates without having the software itself it wont update it obviously... u must have the software itself, and if it doesn thaen manually run the dpkg

---

### Post by Dutch70 on 2008-07-12
open a terminal and run this...
```
sudo dpkg --configure -a 
```

also you may want to check out this page...
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Dutch

---

### Post by kansasnoob on 2008-07-12
Just go to System > Administration > Synasptic Package Manager. then click on the Settings tab. You'll see this:

[ATTACH]77526[/ATTACH]

[ATTACH]77527[/ATTACH]

[ATTACH]77528[/ATTACH]

Then just search for and install the programs you want from synaptic.

Abiword (if you're using Ubuntu with the gnome desktop):

[ATTACH]77529[/ATTACH]

Amarok:

[ATTACH]77530[/ATTACH]

---

### Post by kansasnoob on 2008-07-12
And look here:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

