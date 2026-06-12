---
title: "/bin/sh and rpm matters"
date: 2015-12-21
forum: New to Ubuntu
---

### Post by anna15 on 2015-12-21
Hi, 
I'm trying to install a printer, but it's not trivial at all.

I extracted the repertory but there is ot install instruction on ReadMe. So I tryed to work it with RPM, but it didn't work I don't get why. 
> rpm -i /home/ecodair/Linux_CAPT_PrinterDriver_V270_uk_EN/64-bit_Driver/RPM/cndrvcups-common-3.20-1.x86_64.rpm 
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
attention : Génération d'index manquant(s) 12, merci d'attendre...   =**index generator missing (12), wait please...**
erreur : Dépendances requises:    =**Error : Dependance requests**
    /bin/sh est nécessaire pour cndrvcups-common-3.20-1.x86_64   **=/bin/sh is needed for <File_Name>**
    libatk-1.0.so.0()(64bit) est nécessaire pour cndrvcups-common-3.20-1.x86_64 **=libatk-1.0.so.0()(64bit) is needed for <File_Name>**
What is /bin/sh ? 
Also, I found the command rpm -i on the internet, why is it wrong to use it here ?

---

### Post by steeldriver on 2015-12-21
**rpm** is the **redhat** package manager

Ubuntu (and other Debian derivatives) use **apt** - the advanced package tool

**alien** is a tool that may be able to convert an rpm package to a suitable deb package

/bin/sh is a shell: on Ubuntu, it is (symlinked to) the dash shell by default, it's possible the installer is expecting it to be bash because it is expecting the OS to be redhat-based

EDIT: I just downloaded the driver archive from here: [http://support-au.canon.com.au/contents/AU/EN/0100459602.html](http://support-au.canon.com.au/contents/AU/EN/0100459602.html)

and it appears to have native Debian packages as well

```

$ ls Linux_CAPT_PrinterDriver_V270_uk_EN/64-bit_Driver/Debian/
cndrvcups-capt_2.70-1_amd64.deb  cndrvcups-common_3.20-1_amd64.deb

```

---

### Post by Bucky Ball on 2015-12-21
Might help if you let us know the printer you are trying to install. Are you positive you need to do any of this? Let us know the make and model and we'll be able to give better support. :)

---

### Post by oldos2er on 2015-12-22
CUPS is already installed on desktop Ubuntu, so to configure a printer open Firefox and use the URL [http://localhost:631/](http://localhost:631/)

And as Bucky said, please tell us the make and model of your printer.

---

### Post by buzzingrobot on 2015-12-22
> **anna15 said:**
> Hi, 
Also, I found the command rpm -i on the internet, why is it wrong to use it here ?

To answer that question:  Software for Linux is packaged in archives that contain the actual software components, plus instructions -- scripts -- that are run to place each component in the right location.  This make software installation, even of complex software with hundreds of components, pretty simple.

For historical reasons, more than one method and standard for creating these packages exists. Ubuntu software is packaged in the "deb" format.  You will see file names with the ".deb" extension.  Software for the Red Hat, and related Linux distributions, is packaged in the "rpm" format. 

The two systems are essentially identical in their objectives, but they are incompatible. That's why "rpm- i" is "wrong" for Ubuntu.  It's intended for use on a Red Hat system.

Many printers are easily supported in Ubuntu.  As mentioned earlier, post the manufacturer and model of your printer and someone can likely give you much better guidance.

Also, be wary of quickly following guidance you find on the internet unless it is from a source you believe is reliable and if the guidance applies specifically to your problem and the version of Linux you are using.

---

