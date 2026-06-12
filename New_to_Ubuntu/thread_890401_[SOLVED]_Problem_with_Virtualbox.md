---
title: "[SOLVED] Problem with Virtualbox"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by karthikophobia on 2008-08-15
I Installed Virtualbox on myhardy but when I tried to start a virtual machine, I'm getting the following error message:

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```


I installed 'virtualbox-ose-modules-generic' but still the problem persists

plz help

---

### Post by Pro-reason on 2008-08-15
What do you get if you type "*uname -a*" in a terminal?

---

### Post by karthikophobia on 2008-08-15
Linux BG-203 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux

---

### Post by y@w on 2008-08-15
I'm guesing you just need the modules for your exact kernel. Try:

```
sudo apt-get install virtualbox-ose-modules-generic-`uname -r`
```

---

### Post by karthikophobia on 2008-08-15
> **y@w said:**
> I'm guesing you just need the modules for your exact kernel. Try:

```
sudo apt-get install virtualbox-ose-modules-generic-`uname -r`
```

I got the following message:
```
E: Couldn't find package virtualbox-ose-modules-generic-2.6.24-20-generic
```

I Installed the following packages but still no use:
virtualbox-ose-guest module for linux-image-2.6.24-20-generic
virtualbox-ose-guest module for linux-image-generic
virtualbox-ose module for linux-image-2.6.24-20-generic
virtualbox-ose module for linux-image-generic

---

### Post by Pro-reason on 2008-08-15
There is a mistake there.  Try this:
```

sudo apt-get install **virtualbox-ose-modules-2.6.24-20-generic**

```

Then reboot.

---

### Post by karthikophobia on 2008-08-15
> **Pro-reason said:**
> There is a mistake there.  Try this:
```

sudo apt-get install **virtualbox-ose-modules-2.6.24-20-generic**

```

Then reboot.

as I mentioned above I already installed it.

---

### Post by Ryadt on 2008-08-15
Uninstall the one in the repos and follow this guide to install the latest one.[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

---

### Post by karthikophobia on 2008-08-15
I logged off and logged on again and it works now

thnx everone

---

