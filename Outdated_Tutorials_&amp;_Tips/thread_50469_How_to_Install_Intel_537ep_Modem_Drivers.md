---
title: "How to: Install Intel 537ep Modem Drivers"
date: 2005-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by the_pc_dude on 2005-07-20
do the steps in this thread [http://ubuntuforums.org/showthread.php?t=36762&highlight=Intel+537](http://ubuntuforums.org/showthread.php?t=36762&highlight=Intel+537)


**DO THIS COMMANDS IMPORTANT ** 
Because the module Intel 537 will not load unless specified by user
sudo cp -v /etc/modules /etc/modules.backup

sudo echo Intel537 >> /etc/modules

**THIS COMMAND IS OPTIONAL** 

gedit /etc/modules this is to make sure that  Intel 537 Is there at the end of modules listed to load at startup.

If this tutorial doesn't work try [url]http://ubuntuforums.org/showthread.php?t=37465&highlight=Intel+536I[/url
**One more note if an step doesn't try another step in another tutorial**

---

