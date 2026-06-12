---
title: "How to uninstall a deb package"
date: 2023-07-08
forum: New to Ubuntu
---

### Post by janvi2 on 2023-07-08
some time ago I downloaded ozone.deb and installed by 
 
 > sudo apt install ozone.deb

The commercial licence worked like expected and I set a icon to the favorite bar. Now I like to uninstall this version V2.70e before upgrading to any later version. Unfortunately, the package does not appaer in the „installed“ group of the Gnome Application Manager. 

 
 > locate ozone 

 
 shows, that the package is obviosly installed in 

 
 /opt/SEGGER/ozone

 
 and some minor files in 

 
 /usr/share/doc/ozone

  

 What is the prefered way to uninstall this package ?

---

### Post by Rubi1200 on 2023-07-08
Did you check their instruction manual? Has details on uninstallation and removal of application files:
[https://www.segger.com/downloads/jlink/UM08025_Ozone.pdf](https://www.segger.com/downloads/jlink/UM08025_Ozone.pdf)

---

### Post by janvi2 on 2023-07-08
To be honest: I did not read this hint in the 374 pages manual.
Anyhow the graphical uninstall is not available on my system for whatever reason. 
The command line does the following: 

 sudo dpkg -remove Ozone
dpkg: error: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
jv@JamesWebb:~$ 

Changing the options to 
> sudo dpkg -r Ozone

reports hundreds of
file missing; assuming package has no files currently installed

After this, the package still works fine but dpkg does not know anything about:

>dpkg -s Ozone
>dpkg-query: package 'ozone' is not installed and no information is available
>Use dpkg --info (= dpkg-deb --info) to examine archive files.
>dpkg --info Ozone
>dpkg-deb: error: failed to read archive 'Ozone': No such file or directory

---

### Post by ajgreeny on 2023-07-08
Get rid of that upper case O in the name; it looks as if ***sudo apt -remove ozone*** should do the job.

Don't forget that Linux is case sensitive so O is not o.

---

### Post by janvi2 on 2023-07-08
Also dropped your minus character for options, but its independed from ozone or Ozone.
As the file download was separate, it should be same if using dpckg or apt ?
Invoking the package from commandline is only Ozone not ozone

jv@JamesWebb:~$ sudo apt remove ozone
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package ozone

v@JamesWebb:~$ locate Ozone
/home/jv/.config/SEGGER/Ozone.conf
/home/jv/.local/share/Trash/files/Ozone.deb
/home/jv/.local/share/Trash/files/Ozone_Linux_V270e_x86_64.deb
/home/jv/.local/share/Trash/info/Ozone.deb.trashinfo
/home/jv/.local/share/Trash/info/Ozone_Linux_V270e_x86_64.deb.trashinfo
/home/jv/.local/share/Trash/info/UM08025_Ozone.pdf.trashinfo
/home/jv/Desktop/UM08025_Ozone.pdf
/home/jv/Downloads/Ozone_Linux_V330a_x86_64.deb
/opt/SEGGER/ozone/2.70.5/Ozone
/opt/SEGGER/ozone/2.70.5/Ozone.png
/opt/SEGGER/ozone/2.70.5/Doc/ReleaseOzone.html
/opt/SEGGER/ozone/2.70.5/Doc/UM08025_Ozone.pdf
/usr/bin/Ozone
jv@JamesWebb:~$

---

### Post by Holger_Gehrke on 2023-07-08
I'd use 'dpkg-query -S /opt/SEGGER/ozone/2.70.5/Ozone' to get the actual name of the package and then use that name either with 'apt remove' or 'dpkg -r'.

Holger

---

### Post by ActionParsnip on 2023-07-08
What is the output of
```

dpkg -l | grep -i zone

```

---

### Post by janvi2 on 2023-07-09
jv@JamesWebb:~$ dpkg-query -S /opt/SEGGER/ozone/2.70.5/Ozone
dpkg-query: warning: files list file for package 'libgme0:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libnet-ssleay-perl:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'fonts-smc' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libjpeg8:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libjpeg8:i386' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'gnome-calculator' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libchromaprint1:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libkf5codecs-data' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libxklavier16:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libbcprov-java' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'gir1.2-graphene-1.0:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libpwquality-common' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'automake' miss ......................
dpkg-query: warning: files list file for package 'libwayland-client0:i386' missing; assuming package has no files currently installed
ozone:amd64: /opt/SEGGER/ozone/2.70.5/Ozone

jv@JamesWebb:~$ dpkg -l | grep -i zone
ii  dns-root-data                              2021011101                                      all          DNS root data including root zone and DNSSEC key
ii  libdatetime-timezone-perl                  1:2.51-1+2021e                                  all          framework exposing the Olson time zone database to Perl
ii  ozone:amd64                                2.70.5                                          amd64        SEGGER Ozone
ii  python3-tz                                 2022.1-1ubuntu0.22.04.1                         all          Python3 version of the Olson timezone database
ii  tzdata                                     2023c-0ubuntu0.22.04.2                          all          time zone and daylight-saving time data
jv@JamesWebb:~$

---

### Post by ActionParsnip on 2023-07-09
> **janvi2 said:**
> jv@JamesWebb:~$ dpkg-query -S /opt/SEGGER/ozone/2.70.5/Ozone
dpkg-query: warning: files list file for package 'libgme0:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libnet-ssleay-perl:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'fonts-smc' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libjpeg8:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libjpeg8:i386' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'gnome-calculator' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libchromaprint1:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libkf5codecs-data' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libxklavier16:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libbcprov-java' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'gir1.2-graphene-1.0:amd64' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'libpwquality-common' missing; assuming package has no files currently installed
dpkg-query: warning: files list file for package 'automake' miss ......................
dpkg-query: warning: files list file for package 'libwayland-client0:i386' missing; assuming package has no files currently installed
ozone:amd64: /opt/SEGGER/ozone/2.70.5/Ozone

jv@JamesWebb:~$ dpkg -l | grep -i zone
ii  dns-root-data                              2021011101                                      all          DNS root data including root zone and DNSSEC key
ii  libdatetime-timezone-perl                  1:2.51-1+2021e                                  all          framework exposing the Olson time zone database to Perl
ii  ozone:amd64                                2.70.5                                          amd64        SEGGER Ozone
ii  python3-tz                                 2022.1-1ubuntu0.22.04.1                         all          Python3 version of the Olson timezone database
ii  tzdata                                     2023c-0ubuntu0.22.04.2                          all          time zone and daylight-saving time data
jv@JamesWebb:~$

sudo apt --purge remove ozone:amd64
sudo apt --purge autoremove

---

### Post by janvi2 on 2023-07-09
Always same problem: 

jv@JamesWebb:~$ sudo apt --purge remove ozone:amd64
[sudo] password for jv: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  attr dh-elpa-helper grub-pc-bin libcephfs2 libgfapi0 libgfrpc0 libgfxdr0
  libglusterfs0 libllvm13 libllvm13:i386 librados2 librhash0 python3-dnspython
  python3-gpg python3-markdown python3-requests-toolbelt python3-samba
  python3-tdb tdb-tools
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  ozone*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
28 not fully installed or removed.
After this operation, 57,3 MB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'libgme0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnet-ssleay-perl:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-smc' missing; assuming package has no files currently installed
many many more files .....
and
Errors were encountered while processing:
 libreoffice-common
 grub-efi-amd64
 libreoffice-gnome
 gdm3
 libreoffice-l10n-de
many more ...

I wonder Ozone has nothing to do with libreoffice and there should be no dependecies ?
Without understanding what happened, the old ozone is now away inlcuding the icons.

---

### Post by ActionParsnip on 2023-07-09
> **janvi2 said:**
> Always same problem: 

jv@JamesWebb:~$ sudo apt --purge remove ozone:amd64
[sudo] password for jv: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  attr dh-elpa-helper grub-pc-bin libcephfs2 libgfapi0 libgfrpc0 libgfxdr0
  libglusterfs0 libllvm13 libllvm13:i386 librados2 librhash0 python3-dnspython
  python3-gpg python3-markdown python3-requests-toolbelt python3-samba
  python3-tdb tdb-tools
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  ozone*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
28 not fully installed or removed.
After this operation, 57,3 MB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'libgme0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnet-ssleay-perl:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-smc' missing; assuming package has no files currently installed
many many more files .....
and
Errors were encountered while processing:
 libreoffice-common
 grub-efi-amd64
 libreoffice-gnome
 gdm3
 libreoffice-l10n-de
many more ...

I wonder Ozone has nothing to do with libreoffice and there should be no dependecies ?
Without understanding what happened, the old ozone is now away inlcuding the icons.

```
 
sudo apt --reinstall install libnet-ssleay-perl:amd64

```
Then try the uninstall of the ozone application again

---

