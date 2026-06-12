---
title: "HOWTO: Add bootmisc.sh script to 9.10 (for custom bootup commands)"
date: 2009-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by WattoDaToydarian on 2009-11-12
Hello everyone I just spent over an hour figuring out how to get bootmisc.sh back so I thought I would share it with you.
For those of you that are unfamiliar with bootmisc.sh, it used it be included with Ubuntu in versions 9.04 and earlier. It can be used to store your own custom commands that run early in the boot process. For example in my case I use it to reload all my sound modules for my two sound cards so they load in the order I want them to.

There are two simple steps to adding the script. Note: The script can have any name you want just replace "bootmisc.sh" with your own name.

#1. Make the script.
To get started on the script run this in your terminal:
```
sudo nano /etc/init.d/bootmisc.sh
``` Then press *CTRL+X* then *Y* then *ENTER* when you are done to save it.
After that you have to make it executable by using this command:
```
sudo chmod +x /etc/init.d/bootmisc.sh
```

#2. Add the script to init.
For this step all you have to do is run this in your terminal:
```
sudo update-rc.d bootmisc.sh start 20 2 .
```

There are also two simple steps to removing the script if you need to.

#1. Remove it from init.
For this step all you have to do is run this in your terminal:
```
sudo update-rc.d -f bootmisc.sh remove
```

#2. Delete the script.
Just use this rm command:
```
sudo rm /etc/init.d/bootmisc.sh
```

Thanks for reading and I hope you find this helpful.:popcorn:

---

