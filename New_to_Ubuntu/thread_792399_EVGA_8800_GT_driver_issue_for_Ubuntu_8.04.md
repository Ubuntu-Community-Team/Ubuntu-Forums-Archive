---
title: "EVGA 8800 GT driver issue for Ubuntu 8.04"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-05-12
hi, I installed Ubuntu 8.04 and run 3D applications. But either enabling or disabling the acceleration driver makes it crashed.

Is there anyway to get a driver more "compatible" with Ubuntu?

Thanks

---

### Post by overdrank on 2008-05-12
> **Unewbeginner said:**
> hi, I installed Ubuntu 8.04 and run 3D applications. But either enabling or disabling the acceleration driver makes it crashed.

Is there anyway to get a driver more "compatible" with Ubuntu?

Thanks

Hi and you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by JoshuaRL on 2008-05-12
> **Unewbeginner said:**
> hi, I installed Ubuntu 8.04 and run 3D applications. But either enabling or disabling the acceleration driver makes it crashed.

Is there anyway to get a driver more "compatible" with Ubuntu?

Thanks

Sure man, you need to install the Nvidia drivers.  Go to their site and get the right driver from them.  Download it to your desktop and follow the 5 steps below to get it installed:

**Five Steps to Nvidia Driver Install!**

1).  Reboot the computer and choose Recovery Mode from the GRUB menu.

2).  Move into the Desktop:
```

cd /home/username/Desktop

```
The capitol "D" is important, and "username" is the name of the user that has the file in their desktop.

3).  Find the name of the installer file:
```

ls

```
That's a lowercase L, not a 1.  The file that you downloaded to the Desktop will show up here.  When you use that name in the steps below, make sure you type it exactly.  I'll be using "nvidiainstallerfile.run" as the fake name.

4).  Change permission level of the installer file so it has internet access:
```

chmod +x nvidiainstallerfile.run

```

5).  Run the installer file in a shell:
```

sh nvidiainstallerfile.run

```
Go through all the options, picking the defaults unless you KNOW you need something else.  After that's done, you reboot the computer and the driver should be installed.

Congratulations!

---

### Post by Victormd on 2008-05-12
I have an 8800GT as well and I ran into problems when upgrading from gutsy to hardy. Wouldn't work for anything in this world so I just reinstalled... works like a charm!!!
Installed a clean Hardy (don't recall having to use safe graphics mode), before any attempt to install the graphics card, select all sources in the repositories (system>administration>software sources) then reload (or type sudo apt-get update in the terminal) and reboot. This will "fix" the restricted drivers issue (initially the driver is marked but not in use - at least in my case) and you'll be able to select and install from there with no problem at all!! This worked for me. Later, I broke ubuntu again (different issue) and gave it a shot using envy-ng and it worked just as good. Search for envyng and 3 options should come up. If you're using Ubuntu, install the envyng-gtk. If you're using Kubuntu, install the envyng-qt. Once installed, the program will show under Applications>System Tools.
Run the program and it should install the driver properly.

---

### Post by Unewbeginner on 2008-05-12
> **overdrank said:**
> Hi and you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Hi I just tried Envy but the situation is worse. I use automatic detection and it finished the operation. after I reboot my computer, I can only use low resolution. What should I do...

---

### Post by Unewbeginner on 2008-05-12
> **JoshuaRL said:**
> Sure man, you need to install the Nvidia drivers.  Go to their site and get the right driver from them.  Download it to your desktop and follow the 5 steps below to get it installed:



Hi, I went to EVGA website and can only see drivers for Windows.

---

### Post by jrharvey on 2008-05-12
> **Unewbeginner said:**
> Hi, I went to EVGA website and can only see drivers for Windows.

You should be able to choose your OS when selecting a download.

---

### Post by Unewbeginner on 2008-05-12
> **jrharvey said:**
> You should be able to choose your OS when selecting a download.

Hi I downloaded the driver but The installation is failed. 

ERROR: You appear to be running an X server; please exit X before installing.

How to exit X?

THanks.

---

### Post by Victormd on 2008-05-12
restart in safemode and exit to the terminal

---

### Post by Unewbeginner on 2008-05-12
> **Victormd said:**
> restart in safemode and exit to the terminal

what do you mean "exit to the terminal"? how to make it?

sorry I'm pretty new to Ubuntu.

---

### Post by overdrank on 2008-05-12
> **Unewbeginner said:**
> what do you mean "exit to the terminal"? how to make it?

sorry I'm pretty new to Ubuntu.

Hi and PmDematagoda has paced good direction in this thread #7 
[http://ubuntuforums.org/showthread.php?t=779655](http://ubuntuforums.org/showthread.php?t=779655)

---

### Post by Victormd on 2008-05-12
> **Unewbeginner said:**
> what do you mean "exit to the terminal"? how to make it?

sorry I'm pretty new to Ubuntu.

reboot your machine and from the grub menu, select the second option. If no menu is showing when you restart the computer, hit the ESC key after the BIOS loads and the menu will show up...

---

### Post by Victormd on 2008-05-12
follow the link posted by overdrank... :)

---

### Post by Unewbeginner on 2008-05-13
hello, I installed the driver but it doesn't work. I searched in the forum and find a way to exit X server. But during the installation, the system message is something like "no XXX for this Kernel, now do you want the package build it?" I chose yes, and all the way down the installation is finished. but after I reboot, no change.

Please help ~~~

---

### Post by Victormd on 2008-05-13
> **Unewbeginner said:**
> hello, I installed the driver but it doesn't work. I searched in the forum and find a way to exit X server. But during the installation, the system message is something like "no XXX for this Kernel, now do you want the package build it?" I chose yes, and all the way down the installation is finished. but after I reboot, no change.

Please help ~~~

Did you try using envy-ng to install?

---

### Post by philinux on 2008-05-13
What is shown in

System>Admin>Hardware drivers.

To get my 8600 going I just ticked the box.

---

