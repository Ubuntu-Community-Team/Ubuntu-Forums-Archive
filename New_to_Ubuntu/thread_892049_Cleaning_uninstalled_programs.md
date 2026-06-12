---
title: "Cleaning uninstalled programs"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-08-16
I have a slight issue...I'm addicted to trying out random apps and Ubuntu makes it that much worse with it's package manager...

However, this addiction has led to a, uh, rather messy hard drive. 

It seems even apps uninstalled through the package manager still have remnants sitting in my home directory and probably elsewhere. With proprietary apps I've tried, it's even worse since it seems nothing is keeping track of them.  

I've used Synaptic to remove no longer used dependencies and have used Orphaned Package Remover as well but there's still crap sitting in my computer. 

Is there an easy way to hunt down leftover files and directories and get rid of them or should I just turn "View Hidden Folders" off in Nautilus and stop worrying about it?

---

### Post by dje on 2008-08-16
you can safely delete the hidden directories in your home folder for programs you dont want as these only contain settings although really it doesnt matter ;) as if you ever reinstall the program you will have the settings back if you dont delete them. when removing a program choose "mark for complete removal" or in the terminal:
```
sudo apt-get autoremove --purge *package*
```
you can also periodically run:
```
sudo apt-get autoremove
sudo apt-get clean
```

dje

---

### Post by shatteredmindofbob on 2008-08-17
> **dje said:**
> you can safely delete the hidden directories in your home folder for programs you dont want as these only contain settings although really it doesnt matter ;) as if you ever reinstall the program you will have the settings back if you dont delete them. when removing a program choose "mark for complete removal" or in the terminal:
```
sudo apt-get autoremove --purge *package*
```
you can also periodically run:
```
sudo apt-get autoremove
sudo apt-get clean
```

dje

Thanks. Now, any advice on removing things that I didn't get from the repositories? For example, I'm positive I uninstalled VMWare (prefer Virtualbox) but I still see directories called VMWare floating around...

---

### Post by dje on 2008-08-17
> **shatteredmindofbob said:**
> Thanks. Now, any advice on removing things that I didn't get from the repositories? For example, I'm positive I uninstalled VMWare (prefer Virtualbox) but I still see directories called VMWare floating around...

how did you install VMWare?

dje

---

### Post by DrakeGis on 2008-08-22
I use "complete removal" in Synaptic and I still have the hidden folders in my home directory... why ?????
I also tried autoremove and clean, nothing works.
As example I installed, used and uninstalled anjuta... and unfortunately I still have .anjuta in my home folder. Is there a way to really delete the configuration files ?

---

### Post by ubuntu-freak on 2008-08-22
Just so you know, it can sometimes cause problems if you delete folders (in root) of applications you remove, which were installed by default, problems regarding symlinks etc, so don't do that.
 
Other than that, you will have to remove unwanted hidden folders manually from your home directory, I'm not sure why.

---

### Post by philinux on 2008-08-22
There are two more apps you can install

fslint

and 

cruft


Enjoy :lolflag:

---

### Post by skymera on 2008-08-22
Regards to the post above.

Cruft, what does it do? the files it displays in the terminal are they being deleted?

+ on another note, is your 8600 DDR2 or DDR3?

---

