---
title: "Ubuntu 12.10 : Broken packages"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Tarka Dal on 2013-01-29
I downloaded the tarball for HP Linux Imaging and Printing 
@ [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html) and tried to install and failed. So, I decided to do it the easy way when I found I could not as there were broken packages. I have tried to find a way to clear the broken packages but cannot find any help with Ubuntu 12.10. I tried 12.04 but failed with that. Any help would be appreciated!

---

### Post by omeomi on 2013-01-29
You can first try this command and follow the hints it provides (if any):
```
sudo apt-get install -f
```

If that doesn't work you can boot into recovery mode and choose 'Fix broken packages'

---

### Post by Tarka Dal on 2013-01-29
Does not seem to work.
Also going into recovery mode and "Fix broken packages" does not work.
This is a fresh clean install of Ubuntu done yesterday!

[PHP]clive@Ubuntu:~$ sudo -s
[sudo] password for clive: 
root@Ubuntu:~# sudo apt-get install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-1.0-0-dev wget python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ghostscript is already the newest version.
libdbus-1-dev is already the newest version.
libdbus-1-dev set to manually installed.
libjpeg62-dev is already the newest version.
libsane is already the newest version.
libusb-1.0-0-dev is already the newest version.
libusb-1.0-0-dev set to manually installed.
openssl is already the newest version.
policykit-1 is already the newest version.
policykit-1-gnome is already the newest version.
python is already the newest version.
python-imaging is already the newest version.
python-notify is already the newest version.
python-qt4 is already the newest version.
python-qt4-dbus is already the newest version.
python-reportlab is already the newest version.
sane-utils is already the newest version.
wget is already the newest version.
cups is already the newest version.
cups-bsd is already the newest version.
cups-client is already the newest version.
libcups2 is already the newest version.
libcups2-dev is already the newest version.
libcups2-dev set to manually installed.
python-dbus is already the newest version.
python-gobject is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libcupsimage2-dev : Depends: libtiff-dev
                     Depends: libjpeg8-dev but it is not going to be installed or
                              libjpeg-dev
 libsane-dev : Depends: libjpeg-dev
               Depends: libtiff5-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@Ubuntu:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  comerr-dev krb5-multidev libavahi-client-dev libavahi-common-dev
  libcups2-dev libdbus-1-dev libexif-dev libgcrypt11-dev libgnutls-dev
  libgnutls-openssl27 libgnutlsxx27 libgpg-error-dev libgphoto2-2-dev
  libgssrpc4 libieee1284-3-dev libjbig-dev libkadm5clnt-mit8 libkadm5srv-mit8
  libkdb5-6 libkrb5-dev liblzma-dev libp11-kit-dev libpng12-dev libtasn1-3-dev
  libtiffxx5 libusb-1.0-0-dev libusb-dev libv4l-dev zlib1g-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Ubuntu:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  comerr-dev krb5-multidev libavahi-client-dev libavahi-common-dev
  libcups2-dev libdbus-1-dev libexif-dev libgcrypt11-dev libgnutls-dev
  libgnutls-openssl27 libgnutlsxx27 libgpg-error-dev libgphoto2-2-dev
  libgssrpc4 libieee1284-3-dev libjbig-dev libkadm5clnt-mit8 libkadm5srv-mit8
  libkdb5-6 libkrb5-dev liblzma-dev libp11-kit-dev libpng12-dev libtasn1-3-dev
  libtiffxx5 libusb-1.0-0-dev libusb-dev libv4l-dev zlib1g-dev
0 upgraded, 0 newly installed, 29 to remove and 0 not upgraded.
After this operation, 26.2 MB disk space will be freed.
Do you want to continue [Y/n]? y
Sorry, your system lacks support for the snapshot feature
(Reading database ... 147919 files and directories currently installed.)
Removing libcups2-dev ...
Removing libkrb5-dev ...
Removing krb5-multidev ...
Removing comerr-dev ...
Removing libavahi-client-dev ...
Removing libavahi-common-dev ...
Removing libdbus-1-dev ...
Removing libgphoto2-2-dev ...
Removing libexif-dev ...
Removing libgnutls-dev ...
Removing libgcrypt11-dev ...
Removing libgnutls-openssl27:amd64 ...
Removing libgnutlsxx27:amd64 ...
Removing libgpg-error-dev ...
Removing libkadm5srv-mit8:amd64 ...
Removing libkdb5-6:amd64 ...
Removing libkadm5clnt-mit8:amd64 ...
Removing libgssrpc4:amd64 ...
Removing libieee1284-3-dev ...
Removing libjbig-dev:amd64 ...
Removing liblzma-dev:amd64 ...
Removing libp11-kit-dev ...
Removing libpng12-dev ...
Removing libtasn1-3-dev ...
Removing libtiffxx5:amd64 ...
Removing libusb-1.0-0-dev ...
Removing libusb-dev ...
Removing libv4l-dev ...
Removing zlib1g-dev:amd64 ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 5 removed doc-base files...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@Ubuntu:~# sudo apt-get install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-1.0-0-dev wget python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ghostscript is already the newest version.
libjpeg62-dev is already the newest version.
libsane is already the newest version.
openssl is already the newest version.
policykit-1 is already the newest version.
policykit-1-gnome is already the newest version.
python is already the newest version.
python-imaging is already the newest version.
python-notify is already the newest version.
python-qt4 is already the newest version.
python-qt4-dbus is already the newest version.
python-reportlab is already the newest version.
sane-utils is already the newest version.
wget is already the newest version.
cups is already the newest version.
cups-bsd is already the newest version.
cups-client is already the newest version.
libcups2 is already the newest version.
python-dbus is already the newest version.
python-gobject is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libcupsimage2-dev : Depends: libtiff-dev
                     Depends: libjpeg8-dev but it is not going to be installed or
                              libjpeg-dev
 libsane-dev : Depends: libjpeg-dev
               Depends: libtiff5-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@Ubuntu:~# 
[/PHP]

---

### Post by rburkartjo on 2013-01-29
tar open the spm and use the fix broken packages option

then use this link to install hplip
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

good luck note this link is sometimes a little slow in loading but works

---

### Post by Cheesehead on 2013-01-29
Avoid using --assume-yes. You can use it in a script, but apt's interactive prompts exist for good reason.

The system told you that the problem is one or more of six packages:
> libcupsimage2-dev : Depends: libtiff-dev
                     Depends: libjpeg8-dev but it is not going to be installed or
                              libjpeg-dev
 libsane-dev : Depends: libjpeg-dev
               Depends: libtiff5-dev but it is not going to be installed

libcups2image-dev
libtiff-dev
libjpeg8-dev
libjpeg-dev
libsane-dev
libtiff5-dev

One way to fix it:
Disable all PPAs and third-party repos
sudo apt-get update
sudo apt-get purge all_six_packages_by_name
delete all six packages from /var/cache/apt/archives
sudo apt-get install libcups2image-dev libsane-dev

A better way to fix it:
Mostly the same, but one package at a time instead of all six at once.

---

### Post by Tarka Dal on 2013-01-30
> **rburkartjo said:**
> tar open the spm and use the fix broken packages option

then use this link to install hplip
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

good luck note this link is sometimes a little slow in loading but works

There is no Broken Packages option in the SPM on 12.10!:lolflag:

---

### Post by furything on 2013-01-30
See this link
[http://ubuntuforums.org/showthread.php?t=2109711](http://ubuntuforums.org/showthread.php?t=2109711)

Note 2 posts by me about removing broken packages (dpkg cmd) then ensuring
repos ok do the apt-get ones

Always try and use the package gui tools to find what you want as they use the up to date packages for your distro.

This should get you back to a clean starting position at least.

---

### Post by Tarka Dal on 2013-01-30
Thanks furything. I found the "Fix Broken Packages" on the new SPM it's in the edit section at the bottom. I tried this then downloaded the file from  rburkartjo's suggestion and it now works...Thanks everybody!:popcorn:

---

### Post by furything on 2013-01-30
Glad you are all fixed.:cool:

Please remember to mark thread as solved?

---

