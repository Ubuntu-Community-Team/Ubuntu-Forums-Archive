---
title: "Virtualbox Issue"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by NOLU on 2008-08-11
Hello.

I had VB using 7.10 before I upgraded to 8.04. 

Now VB is installed but when I click on VB and run XP, I get this message:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Now in the past I think I was meant to go to User and Groups and tick VB but each time I go to User and Groups, I click Manage Groups and find all that is listed next as unhighlighted.

If I then go back to User Groups, I have to press an unlock button that then shows all listed as highlighted so I can click on the VB option but my name is already ticked which I think it's how it should be.

I still can't start the XP because of the error message so any idea what I can do?

Thanks.

---

### Post by Ryadt on 2008-08-11
Uninstall the one in the repos and follow this guide to install the latest version.[http://ubuntuforums.org/showthread.php?t=828927&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=828927&highlight=virtualbox)

---

### Post by cosine352 on 2008-08-11
I had the same problem before. I solved it as shown below.

> sudo aptitude install linux-headers-$(uname -r)

Then reinstall virtualbox. (I got the .deb file from
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI))

hope this helps.

---

### Post by .nedberg on 2008-08-11
You updated your kernel when you updated from 7.10.

```
sudo /etc/init.d/vboxdrv setup
```
should get everything back to normal. It will rebulid the vbox modules.

---

