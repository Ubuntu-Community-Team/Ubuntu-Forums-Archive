---
title: "Is it necessary to use update and/or upgrade commands before installing a program?"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by arroy_0209 on 2013-10-10
1. I am willing to install k3b in my ubuntu12.03 (gnome). Is it necessary to use the "sudo apt-get update && sudo apt-get dist-upgrade" commands just before issuing the command to install (sudo apt-get install k3b)? Or is it necessary to use the update and upgrade commands after installing k3b (but before using the newly installed package) in my case?

2. In general when (other than at the time of installing programs) shoud one think of issuing the commands of update and upgrade? periodically? 

3. What about receiving "important security updates" from ubuntu and updating those packages? Do I need to use the upgrade command after those processes?

---

### Post by mastablasta on 2013-10-10
you dont' need to use those commands. they are what update manager runs when it performs updates (it's just a command line interface way of doing the same thing). you can just install form software center. i think update command runs when you open the center. i could be wrong though...

---

### Post by 3rdalbum on 2013-10-10
The "update" command just ensures Ubuntu knows what the current software versions is. If your software won't download, try this.

The "upgrade" command upgrades every upgradable package to the latest versions known by Ubuntu.

Neither command is necessary before installing a new package.

---

