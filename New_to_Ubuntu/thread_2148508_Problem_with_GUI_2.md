---
title: "Problem with GUI 2"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by Banshee159 on 2013-05-25
hello guys, there is already thread a regarding this matter. The problem is my GUI go screwed after i installed nvidia graphics recommended version drivers when i saw that the beta experimental drivers were being used .When i rebooted it i was taken to the CLI(full screen cmd window which asked me for my login and password. After entering it , it asks me for codes. Some user(Galgalesh) said that type startx.        Result of typing sudo startx:                                                                                                                                                                                                                                                                        It says initializing "Program name" Nvidia API mismatch:P the NVidia kernel module has version 310.14 but this NVidia driver component has version 304.88. Pls make sure that the Kernel module and all NVidia drivers component have the same version. Fatal server error no "some word" found(EE)   Server terminated with error(1). Closing log file. This error comes even after i installed ppa-purge and removed the drivers.                                                                                                                                                                                                                                                                                                  Code for purge:  
 sudo apt-get install ppa-purge

sudo ppa-purge ppa:ubuntu-x-swat/x-updates

---

### Post by grahammechanical on 2013-05-25
What version of Ubuntu? If 13.04 select Advanced Options for Ubuntu at the Grub boot menu and then select Recovery Mode. Next select Resume. That may get you to a desktop running on llvmpipe video driver where you can experiment with other video drivers from Additional Drivers tab in Software & Updates.

Regards.

---

