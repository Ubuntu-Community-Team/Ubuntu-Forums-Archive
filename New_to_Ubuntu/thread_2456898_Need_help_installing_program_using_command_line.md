---
title: "Need help installing program using command line"
date: 2021-01-21
forum: New to Ubuntu
---

### Post by jmichaels29 on 2021-01-21
I'm attempting to install the beta version of Gimp with these instructions at this page:  [https://ubuntuhandbook.org/index.php/2020/11/install-gimp-2-99-2-ubuntu-20-04/](https://ubuntuhandbook.org/index.php/2020/11/install-gimp-2-99-2-ubuntu-20-04/)

Here is a copy and paste of what happened in my terminal:

```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ sudo apt install flatpak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-mutter-5 libboost-date-time1.67.0 libboost-iostreams1.67.0
  libboost-locale1.67.0 libboost-system1.67.0 libboost-thread1.67.0
  libcodec2-0.8.1 libde265-0 libdevel-globaldestruction-perl libdns-export1104
  libdns1104 libdvdread4 libfprint-2-tod1 libgnome-desktop-3-18 libgspell-1-1
  libheif1 libicu63 libisc-export1100 libisc1100 libisl21 libllvm10
  liblwres161 libmutter-5-0 libmypaint-1.5-1 libmypaint-common libmysofa0
  libpoppler90 libprocps7 linux-headers-5.4.0-60
  linux-headers-5.4.0-60-generic linux-image-5.4.0-60-generic
  linux-modules-5.4.0-60-generic linux-modules-extra-5.4.0-60-generic
  python3-asn1crypto ruby-did-you-mean
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  flatpak
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 1,066 kB of archives.
After this operation, 5,713 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 flatpak amd64 1.6.5-0ubuntu0.1 [1,066 kB]
Fetched 1,066 kB in 1s (906 kB/s)     
Selecting previously unselected package flatpak.
(Reading database ... 266809 files and directories currently installed.)
Preparing to unpack .../flatpak_1.6.5-0ubuntu0.1_amd64.deb ...
Unpacking flatpak (1.6.5-0ubuntu0.1) ...
Setting up flatpak (1.6.5-0ubuntu0.1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for dbus (1.12.16-2ubuntu2.1) ...
Processing triggers for doc-base (0.10.9) ...
Processing 1 added doc-base file...
michael@michael-HP-EliteDesk-800-G1-SFF:~$ flatpak remote-add --user flathub-beta [https://flathub.org/beta-repo/flathub-beta.flatpakrepo](https://flathub.org/beta-repo/flathub-beta.flatpakrepo)

Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/michael/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

michael@michael-HP-EliteDesk-800-G1-SFF:~$ flatpak install --user flathub-beta org.gimp.GIMP

Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/michael/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

Looking for matches&#8230;
error: The application org.gimp.GIMP/x86_64/beta requires the runtime org.gnome.Platform/x86_64/3.38 which was not found
michael@michael-HP-EliteDesk-800-G1-SFF:~$
```

---

### Post by dakotahross88 on 2021-01-21
did you for sure install a 64 bit version?

---

### Post by dakotahross88 on 2021-01-21
heres a similar issue. > resolved
[runtime/org.gnome.Sdk/x86_64/3.20 fails to install · Issue #96 · flatpak/flatpak · GitHub]("https://github.com/flatpak/flatpak/issues/96")

different OS, but same error and they resolved it. seems to be a flatpak issue.

---

