---
title: "Mystery entry"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by nitromorz on 2013-01-16
OK so hear is my silly question. 
Ubuntu 12.04 (also xubuntu also kde plasma)  I was just looking at the 'disc usage analyser' and noticed that there was entry for PlayOnLinux at some 577.1 mb in home files. That's fine but I don't recall installing it, nor is there any confirmation in synaptic which says I don't have it installed. It appears prefixed dot (.PlayOnLinux).
It's no great panic, just wondering if anybody could explain?

---

### Post by Frogs Hair on 2013-01-16
Hello and Welcome

Are you an only user ? Installing applications requires a password so are you sure you didn't want to check out Play on Linux and then remove it. I don't how a disk volume would have been created because it would not be there by default.

---

### Post by nitromorz on 2013-01-16
Hi Frogs, yes only user and I don't mind it being there but if it's installed why no-show in synaptic?
Sound of head scratching...

---

### Post by iMac71 on 2013-01-16
do you get any output by typing```
which -a playonlinux
```in the Terminal?

---

### Post by nitromorz on 2013-01-16
Hi iMac, no, afraid not no output on that.  Maybe I should install it from synaptic and then uninstall just to see what would happen.

---

### Post by nitromorz on 2013-01-16
Hmm just wondering this, this is a remix build from LXF Towers, I wonder if ... but even so it should be in synaptic surely.

---

### Post by audiomick on 2013-01-16
All things being equal, Synaptic should know what is installed, but it is technically possible for something to be installed and Synaptic not to know about it if it was installed from scratch not using the package manager, for instance, or if the list of installed packages has somehow gotten messed up. 

I think your idea of installing and then purging is possibly worth a try.

---

### Post by nitromorz on 2013-01-16
Hi audiomick, bit weird really. It's the full package too itunes, c drive, wine prefix etc.. I run 'autoclean' and check on orphaned packages fairly regularly, can't think how it has escaped.

---

### Post by nitromorz on 2013-01-16
If I use synaptic to install PlayOnLinux it may well write a second entry as it doesn't know the first one is there. You know what, thanks people, I think I will just leave well alone.

---

