---
title: "VirtualBox Permissions"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-07-07
I was trying to install windows 98 into virtual box. When I clicked to start the virtual box this error popped up:


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I went to /dev/vboxdrv to try to change the permissions on the file, but I cant because I'm not root. Can someone help? Thanks.

---

### Post by wolfen69 on 2008-07-07
go to system>admin>users and groups. then unlock, manage groups, vboxusers, properties and check off your name. then reboot. (log out may work)

---

### Post by wolfen69 on 2008-07-07
you thanked me before i could edit my post. i corrected an error.

---

### Post by redfox1160 on 2008-07-07
now this error is popping up:


The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by redfox1160 on 2008-07-07
help

---

### Post by redfox1160 on 2008-07-07
> **redfox1160 said:**
> now this error is popping up:


The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

help please!

---

### Post by wolfen69 on 2008-07-07
just go to synaptic and completely remove it.  then go [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") to get the .deb file. click to install. if that doesnt work, then you'll probably have to delete your .virtualbox dir, then re-install.

i dont use virtualbox any more, as i find just popping in an old drive and doing what you want, a much better experience. vbox is cool, but a real install is always best.

---

### Post by BGFG on 2008-07-08
Hey, how did you install VirtualBox ? with sudo, or did you go to the site and get the .deb ?
I'd suggest you try what it says, try 

```
sudo apt-get --purge VirtualBox
```

to completly remove VB then reinstall. I recently installed VB on my system and successfully installed XP.
I'm using Hardy 8.04 and i installed it using the .deb file i downloaded from the VB site.


Umm......... what he ^ said  :)

---

### Post by redfox1160 on 2008-07-08
I don't know how to run it after I install it from the deb file.

---

### Post by BGFG on 2008-07-08
Do you mean use it or run it from the menu ? it should be in Applications>>System Tools>>SunVB if it's not there then the menu hasn't refreshed yet.

---

### Post by BGFG on 2008-07-08
Hi Wolfen69, if the menu hasn't refreshed would restarting X help ?

---

### Post by finni on 2009-02-14
> **redfox1160 said:**
> now this error is popping up:


The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I just reinstalled the Virtualbox (downloaded from the sun site) and it recompiled the VB kernel module and now VB works again. Maybe this works for you too. :popcorn:

---

