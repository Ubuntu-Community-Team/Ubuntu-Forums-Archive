---
title: "Downloading and installing wine deb package"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by dwhitney67 on 2008-09-09
I want to download the .deb file for "wine" whilst operating under WinXP.  Where can I go to get this package?

After I download the package, I will transfer it to my Ubuntu 8.04 system via a Samba share I have set up.

Once the package is on my Ubuntu system, what command do I run to install the package?

P.S.  My Ubuntu system does not have internet access at this very moment.  I only have access to the internet via my WinXP system.

---

### Post by Casper Hansen on 2008-09-09
Just go to: 

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

and download the .deb in a folder which is shared or just put it on a USB-pen.

---

### Post by kpkeerthi on 2008-09-09
Download the latest wine package from here: [http://www.getdeb.net/release/3171](http://www.getdeb.net/release/3171)

1. Copy the deb file to ~/Temp
2. cd ~/Temp
3. To install the deb
```
sudo dpkg -i *.deb
```
You could just double-click on the deb file as well and it should being the installation.

---

### Post by SunnyRabbiera on 2008-09-09
Right, as ubuntu has a built in package installer called gdebi.
If you download your .deb file it should install very similar to a .exe installer.

---

### Post by dwhitney67 on 2008-09-09
Apparently "wine" is dependent upon "binfmt-support" and "winbind".  Any ideas where I may get these packages?  Does Ubuntu/Canonical not have a repository where I can get the latest supported .deb packages?

---

### Post by SunnyRabbiera on 2008-09-09
> **dwhitney67 said:**
> Apparently "wine" is dependent upon "binfmt-support" and "winbind".  Any ideas where I may get these packages?  Does Ubuntu/Canonical not have a repository where I can get the latest supported .deb packages?

you should be able to get those packages via windows too, search this site:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

now as for connection issue, atre you using wireless?
and are you trying to install a windows driver of some kind under ubuntu?
fraid it doesnt work that way.

---

### Post by Casper Hansen on 2008-09-09
Just a little question. Why haven't you got Internet connection to your Ubuntu machine?

---

### Post by dwhitney67 on 2008-09-09
Actually I am trying to get a wireless CDMA USB adapter (C-motech CCU-680) to work with Ubuntu (and I haven't tried very hard yet!)

I thought I would take a stab at trying to run the application that came with the CCU-680 with Wine to see if it would detect the USB adapter.

Right now I only have internet connection (using the CCU-680) under WinXP, which I am running as a guest OS under VMware Server 2.0 (beta).

On the side, I been wondering if there is a way to tunnel IP traffic from Ubuntu through the WinXP guest OS.  It would be nice to obtain some .deb packages that I am missing (e.g. connect-proxy).

---

