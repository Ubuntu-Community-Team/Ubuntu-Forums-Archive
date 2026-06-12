---
title: "[tutorial] Install/Upgrade to ATI linux driver 8.42 and activate Compiz-Fusion"
date: 2007-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by MilaNL on 2007-10-26
For everyone who wants to install Ati Linux Driver 8.42 and activate Compiz Fusion on Ubuntu 7.10:
First, download the driver [here]("http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run").

OK first you will have to remove the old drivers. Do this via the Restricted Driver Manager. Just uncheck the ATI drivers, and restart (it will restart with the mesa drivers in low resolution.. dont worry!).
Now, in the terminal, go to the folder where the new Ati linux driver installer is in. Then do the following:
```
$ sudo apt-get update
$ sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic
$ sudo bash ati-driver-installer-8.42.3*.run --buildpkg Ubuntu/7.10
$ gksudo gedit /etc/default/linux-restricted-modules-common
```
now textedit will come. Somewhere in the document, you see DISABLED_MODULES="". Make it DISABLED_MODULES="fglrx".
If there already is something behind DISABLED_MODULES="", just add fglrx to it (i.e. DISABLED_MODULES="hello fglrx").
Then do this:
```
$ sudo dpkg -i xorg-driver-fglrx_8.42.3-1*.deb \
fglrx-kernel-source_8.42.3-1*.deb \
fglrx-amdcccle_8.42.3-1*.deb 
```
Then go to the restricted driver manager again, and check the ATI drivers again.
Restart the computer, and ATI linux drivers 8.42 should work!
You can check this by typing "fglrxinfo" in the terminal. If the output contains:
OpenGL version string: 2.0.6958 Release
you have succesfully installed 8.42.

Now let's get Compiz-Fusion work.
Go to a terminal and type:
```
$ gksudo gedit /usr/bin/compiz 
```
then at the end of WHITELIST, type fglrx, so this is in it:
```
# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"
```
Then type this in a terminal:
```
$ gksudo gedit /etc/X11/xorg.conf 
```
Now, in section Extensions, set option Composite to Enabled. Standard it's 0.
So make it this:
```
Section "Extensions"
   Option      "Composite"   "Enabled"
EndSection
```

now restart (X) and Compiz-Fusion should work!

---

