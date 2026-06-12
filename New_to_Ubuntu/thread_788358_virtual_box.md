---
title: "virtual box"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Doby on 2008-05-09
I have windows xp running in a virtual box on my ubuntu 7.10 computer.  I was wondering if anyone knew how to get the virtual machine to talk to a external hard drive and or a xbox 360?  I have tried fuppes for the 360 streaming but have not been able to get the 360 to recognize my computer.

---

### Post by MattBD on 2008-05-09
Are you connecting via USB? If so, are you using the version of VirtualBox from the repositories?

---

### Post by Doby on 2008-05-11
yeah my external is on usb.  But I'm not sure about the repositories.  What are they so I can check?

---

### Post by mikewhatever on 2008-05-11
> **Doby said:**
> yeah my external is on usb.  But I'm not sure about the repositories.  What are they so I can check?

How did you install Virtual Box? From an installation file you downloaded from the home site, or using the package manager.
Read here about repositories --> [https://help.ubuntu.com/community/Repositories?highlight=%28repositories%29](https://help.ubuntu.com/community/Repositories?highlight=%28repositories%29)

---

### Post by MattBD on 2008-05-11
The version of VirtualBox in the repositories is the Open Source Edition, which doesn't support USB connections. If you need USB support, you need to use the closed-source version. This is free for personal use, and can be downloaded from [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI) - it includes a deb package specifically for Ubuntu Hardy.

---

### Post by Doby on 2008-05-14
Yeah i installed virtual box using the package manager.

---

### Post by MattBD on 2008-05-16
> **Doby said:**
> Yeah i installed virtual box using the package manager.

In that case, first of all you need to uninstall it using the following:
```
sudo apt-get remove virtualbox-ose
```
Then grab the closed-source edition from [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)
There's a deb package specifically for Ubuntu, both x86 and AMD64 versions of both Hardy and Gutsy, so get the one appropriate for your system. You should then be able to install it using Gdebi - just look for the downloaded package in your /home directoryand click on it, and it should install. Alternatively, if you want to use the command line, make sure it's the only deb package in your /home directory and enter the following:
```
sudo dpkg -i *.deb
```
Now you have the closed-source version installed, you should be able to use USB fine with it.

---

