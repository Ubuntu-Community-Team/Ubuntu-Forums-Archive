---
title: "&quot;system settings&quot; GUI forced onto desktop"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by cml6182 on 2013-02-28
I updated Ubuntu 12.04 and I thought everything was fine. But, I just learned that when I activate anything that would have to do with "system settings", the system settings GUI forces itself onto my desktop. Once it is on my desktop, if I close it, it will pop back up right away. And, if I try to select some of the settings it will either not display them or push them into the background after a second. The only way I have been able to get it off the screen is to restart.

Any help would be greatly appreciated and sorry if this is something that has already been solved, I just wasn't able to find anything like this when I searched.

---

### Post by Frogs Hair on 2013-02-28
Try the following. ```
sudo apt-get install --reinstall gnome-control-center
```

---

### Post by cml6182 on 2013-02-28
I think the code did what it was supposed to do but the problem is still persistent. Here is the terminal output just in case that helps:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/662 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 220687 files and directories currently installed.)
Preparing to replace gnome-control-center 1:3.4.2-0ubuntu0.10 (using .../gnome-control-center_1%3a3.4.2-0ubuntu0.10_i386.deb) ...
Unpacking replacement gnome-control-center ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up gnome-control-center (1:3.4.2-0ubuntu0.10) ...

---

