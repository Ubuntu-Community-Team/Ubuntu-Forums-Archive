---
title: "How to install the latest ATi Drivers (8.24.8)"
date: 2006-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by xXx 0wn3d xXx on 2006-04-14
In case you already didn't know, you need an ATi card for this. Do what follows to install and use the latest ATi Linux Drivers. If you are running x64 ubuntu, you are in luck. There are drivers for you :)

**1.**Go to: [ The ATi Linux Drivers Download Page ](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300) and Select "Linux Display Drivers and Software."

**2.** Select the type of vid card that you have.

**3.** You shoud see something like "ATI Proprietary Linux x86 Display Drivers for XFREE86 / X. Org Version 8.24.8" <= something like that, click the link.

**4.** Scroll down the page and select the first download. It should be about 34.6 MB.

**5.** After it is done downloading, make sure it is in your home directory.

**6.** Now right click the file. It should be something like "ati-driver-installer-8.24.8-x86.run" but it can be different. 

**7.** When you are at the menu, click the "Permissions" tab. Check "Execute" and also anything else on the owner row if it is not checked.

**8.** Open terminal: Applications > Accessories > Terminal.

**9.** Login as root. 

> sudo su

**10.** Type the following in terminal:
>  ./ati-driver-installer-8.24.8-x86.run  
You can/should check the name of the file and replace what I said above if it is different.

**11** You should be at an ati window. Install Driver 8.24.8 on X.org 6.8.x shoud be selected. Click continue.

**12.** Click agree and it will install the new drivers. This could take betweem 1-5 minutes depending on your computer.

**13.** You should see that it is done and a dialogue box that says you should reboot.

**14.** Reboot and enjoy the new drivers :)

---

