---
title: "Install / Uninstall ALL programs?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-11
How come certain programs dont show up in the add/remove dialog? I set the filter to see only "installed programs" and I dont see cairo dock and gnome do in there. Even though cairdo dock is installed and I can launch it from the apps menu, and gnome do I thought I removed using apt-get -purge remove. However, I also still get updates for gnome do and gnome-do-plugins even though, I dont have them installed? Weird!

---

### Post by Thelasko on 2008-08-11
The add/remove programs menu is an (overly?) simplified version of the synaptic package manager.  It's designed to make adding and removing programs simple for beginners.  The synaptic package manager will show you all of the program available, including all libraries and sub-programs.  To access it, go to System>Administration>Synaptic Package Manager.

---

### Post by llama320 on 2008-08-11
to stop the updates from coming, you can remove the sources that you added when you installed gnome-do by going into synaptic > settings > repositories > third party software

Also, to remove unnecessary stuff on your hard drive, 

```
sudo apt-get autoremove
```

and

```
sudo apt-get autoclean
``` 

Good Luck

---

