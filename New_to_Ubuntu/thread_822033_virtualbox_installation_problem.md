---
title: "virtualbox installation problem"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by shamusl on 2008-06-07
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

I installed:

```
virtualbox-ose-guest module for linux-image-2.6.24-17-386
```

and I don't know what I did wrong, does anybody know what I'm missing?

(I'm running 8.04 with all updates installed)

---

### Post by Novus on 2008-06-07
I ran into this problem too.. a while ago.. I think I only had to install all 4 virtualbox-ose-modules-2.6.24-17-* in synaptic.. then all worked fine

---

### Post by ibuclaw on 2008-06-07
What is the output of this command?
```
uname -r
```
Chances are, you are running the latest kernel in the Ubuntu repository.
That will be the **2.6.24-18-generic** kernel. So the "24-17" modules won't work with it.


If you are in dia need to run VirtualBox now, uninstall all things named virtualbox in the repository.
Then download the official Ubuntu 8.04 (closed source) binary [here.]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

Double click on the downloaded .deb file to run GDebi and it will install.
Then open up a terminal and paste this command to build the vbox modules.
```
/etc/init.d/vboxdrv setup
```
And add yourself to the vbox group.
```
sudo usermod -a -G vboxusers **username**
```
Replace "username" with your actual username.

Then logout and login again.
Now VirtualBox will run.

Regards
Iain

---

### Post by shamusl on 2008-06-07
> **tinivole said:**
> What is the output of this command?
```
uname -r
```
Chances are, you are running the latest kernel in the Ubuntu repository.
That will be the **2.6.24-18-generic** kernel. So the "24-17" modules won't work with it.


If you are in dia need to run VirtualBox now, uninstall all things named virtualbox in the repository.
Then download the official Ubuntu 8.04 (closed source) binary [here.]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

Double click on the downloaded .deb file to run GDebi and it will install.
Then open up a terminal and paste this command to build the vbox modules.
```
/etc/init.d/vboxdrv setup
```
And add yourself to the vbox group.
```
sudo usermod -a -G vboxusers **username**
```
Replace "username" with your actual username.

Then logout and login again.
Now VirtualBox will run.

Regards
Iain

```
shamus@shamus-desktop:~$ /etc/init.d/vboxdrv setup
open: Permission denied
 * Stopping VirtualBox kernel module                                            
open: Permission denied
 * Cannot unload module vboxdrv

```

The above did not help, any further help would be much appreciated.

---

### Post by quelx on 2008-06-07
```
[COLOR="Red"]sudo[/COLOR] /etc/init.d/vboxdrv setup
```

---

### Post by unicorn_2003_1 on 2008-06-07
If you just download the .deb file from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads), there will be no problem. Unlike the OSE version which is in Ubuntu's repository, this compilation will do the kernel module and usergroup adding thing itself.

---

