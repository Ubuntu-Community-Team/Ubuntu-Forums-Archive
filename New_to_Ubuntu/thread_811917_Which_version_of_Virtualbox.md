---
title: "Which version of Virtualbox?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Benbow on 2008-05-29
Which version of VB works on Hardy? I am desperately in need of help here as I have tried and failed many time to install Virtualbox. Thanks.

---

### Post by wolfen69 on 2008-05-29
[Virtualbox]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

---

### Post by NikoC on 2008-05-29
Download .deb package from website posted in previous post and double click the package to install..

---

### Post by shifty_powers on 2008-05-29
so did the ose version in the repositories fail to install?

---

### Post by Benbow on 2008-05-29
The version suggested failed to install - this gets worse!

---

### Post by Xerp on 2008-05-29
I installed Virtual Box straight from Synaptic on HH and it works great. What is the specific error you are facing?

(Version 1.5.6_ose)

Just for kicks I removed it and then reinstalled. Worked fine.

---

### Post by Benbow on 2008-05-29
Ok, done that but when I run I get this:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Xerp on 2008-05-29
And I take it you have installed the virtualbox-ose-modules package for your kernel?

---

### Post by Benbow on 2008-05-29
Yes but do I have to tnstall the guest modules as well?

---

### Post by Xerp on 2008-05-29
Try this:

> sudo aptitude install virtualbox-ose-modules-generic

---

### Post by Benbow on 2008-05-29
I think I must have tried everything and restarted after each - still get :

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code:
0x80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

