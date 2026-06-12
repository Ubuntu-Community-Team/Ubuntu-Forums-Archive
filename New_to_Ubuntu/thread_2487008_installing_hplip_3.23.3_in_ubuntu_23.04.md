---
title: "installing hplip 3.23.3 in ubuntu 23.04"
date: 2023-05-19
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2023-05-19
1.i did this 
wget [https://sourceforge.net/projects/hplip/files/hplip/3.23.3/hplip-3.23.3.run/download](https://sourceforge.net/projects/hplip/files/hplip/3.23.3/hplip-3.23.3.run/download) -O hplip-3.23.3.run
2.then i did this
 sudo[FONT=Verdana] [/FONT][FONT=Verdana]chmod[/FONT][FONT=Verdana] +x hplip-3.23.3.run
3.then 
[/FONT]sudo[FONT=Verdana] ./hplip-3.23.3.run
then i got this message
[/FONT]warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: make (make - GNU make utility to maintain groups of programs)
warning: Missing REQUIRED dependency: libpthread (libpthread - POSIX threads library)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: python3-devel (Python devel - Python development files)
warning: Missing REQUIRED dependency: libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency: libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency: python3-pyqt4 (PyQt 4- Qt interface for Python (for Qt version 4.x))
warning: This installer cannot install 'python3-pyqt4' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer
How do you install this dependcies?
Is sudo apt-get command the way to do this? thx for help

---

### Post by idmbe on 2023-05-23
for hplip type this::
```
 sudo apt install hplip
```
And any required dependencies will come over automatically

That for GUI tool::
```
sudo apt install hplip-gui
```

For plugin just type and follow the instructions:
```
hp-plugin
```

---

