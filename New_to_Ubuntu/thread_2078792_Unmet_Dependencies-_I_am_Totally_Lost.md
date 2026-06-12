---
title: "Unmet Dependencies- I am Totally Lost"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by SuperFreak on 2012-10-31
I have a broken package:Multi-arch versions of former ia32-libraries
I tried reinstalling ia32-libraries but I am unable to. I also found trying to update the following errors preventing me from updating:


The following packages have unmet dependencies:

ia32-libs-multiarch:i386: Depends: gtk2-engines-oxygen but it is not installed
                          Depends: libaio1 but it is not installed
                          Depends: libsdl-net1.2 but it is not installed
                          Depends: libssl0.9.8 but it is not installed
                          Depends: libstdc++5 but it is not installed
                          Depends: xaw3dg but it is not installed

Tried installing one of these and received another error message

Any help would be most welcome

---

### Post by NikTh on 2012-10-31
Hi , 

have you tried ```
sudo apt-get install -f
```
? 

Thanks

---

### Post by SuperFreak on 2012-10-31
I did try it earlier and get this error message:

```
(Reading database ... 307692 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.22-7ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb (--unpack):
 './lib/udev/rules.d/40-libsane.rules' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by karlstad on 2012-10-31
> **SuperFreak said:**
> I did try it earlier and get this error message:

```
(Reading database ... 307692 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.22-7ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb (--unpack):
 './lib/udev/rules.d/40-libsane.rules' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Try
```
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get -f install
```

That should clear out APT's cache, redownload the files and try to install the dependencies again.

---

### Post by SuperFreak on 2012-10-31
@karlstad Thanks for your help but I am still getting error message about libsane


```
(Reading database ... 307692 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.22-7ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb (--unpack):
 './lib/udev/rules.d/40-libsane.rules' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by karlstad on 2012-10-31
Strange. What does 

```
apt-cache show libsane:i386
```

tell you?

---

### Post by SuperFreak on 2012-10-31
```
desktop:~$ apt-cache show libsane:i386
Package: libsane
Priority: optional
Section: libs
Installed-Size: 8304
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Julien BLACHE <jblache@debian.org>
Architecture: i386
Source: sane-backends
Version: 1.0.22-7ubuntu1
Replaces: libsane-extras (<< 1.0.18.14)
Depends: adduser (>= 3.47), libsane-common (= 1.0.22-7ubuntu1), udev (>= 0.88-1), acl (>= 2.2.49-4), libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.11), libgphoto2-2 (>= 2.4.10.1), libgphoto2-port0 (>= 2.4.10.1), libieee1284-3, libjpeg8 (>= 8c), libtiff4, libusb-0.1-4 (>= 2:0.1.12), libv4l-0 (>= 0.5.0)
Pre-Depends: multiarch-support
Suggests: avahi-daemon, hpoj, hplip, libsane-extras (>= 1.0.22.1), sane-utils (>= 1.0.22-7ubuntu1)
Filename: pool/main/s/sane-backends/libsane_1.0.22-7ubuntu1_i386.deb
Size: 3553810
MD5sum: 75e73058da1b136442383e9f9d413a42
SHA1: de223e83e6d118883e788fab6871e7a94ef467c7
SHA256: 0566f45d24321b2fc4ccee8e6ce22aa322c83be76121dd23b557167bbb38e70e
Description-en: API library for scanners
 SANE stands for "Scanner Access Now Easy" and is an application
 programming interface (API) that provides standardized access to any
 raster image scanner hardware (flatbed scanner, hand-held scanner,
 video- and still-cameras, frame-grabbers, etc.). The SANE standard is
 free and its discussion and development are open to everybody. The
 current source code is written to support several operating systems,
 including GNU/Linux, OS/2, Win32 and various Unices and is available
 under the GNU General Public License (commercial applications and
 backends are welcome, too, however).
 .
 This package includes the backends for many scanners. A libsane-extras
 package containing some not-yet-included backends is available separately.
 .
 Graphical frontends for sane are available in the packages sane and
 xsane. Command line frontend scanimage, saned and sane-find-scanner are
 available in the sane-utils package.
Multi-Arch: same
Homepage: http://www.sane-project.org
Description-md5: 2e25d5fd377d34639732efd0cee2566b
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, print-server, ubuntu-usb, kubuntu-desktop, kubuntu-active-desktop, kubuntu-active, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-core, ubuntustudio-desktop

```

I tried Xsane and scanning works. Printing also works

---

### Post by SuperFreak on 2012-10-31
Everything seems to be working, internet, WINE, printer, Libreoffice,etc but I can't update the system anymore. Get the error messages posted earlier
One program that used a very old version of Sun Java no longer works but it wasn't too important


Would this work? Taken from a similar problem/solution posted on the net:

sudo dpkg -r libsane_1.0.22-7ubuntu1_i386.deb
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

[http://askubuntu.com/questions/171205/e-sub-process-usr-bin-dpkg-returned-an-error-code-1]("http://askubuntu.com/questions/171205/e-sub-process-usr-bin-dpkg-returned-an-error-code-1")

---

### Post by karlstad on 2012-10-31
> **SuperFreak said:**
> Everything seems to be working, internet, WINE, printer, Libreoffice,etc but I can't update the system anymore. Get the error messages posted earlier
One program that used a very old version of Sun Java no longer works but it wasn't too important

Well if you really don't need the libsane:i386 package, you could always try "removing" it.

```
sudo apt-get remove libsane:i386
```

---

### Post by SuperFreak on 2012-10-31
I might do that but see my last post, I edited it while you were posting

---

### Post by karlstad on 2012-10-31
> **SuperFreak said:**
> I might do that but see my last post, I edited it while you were posting

Ah. In theory, that could work but not necessarily. Do you get any different kind of errors now? What if you do the

```
 sudo apt-get clean && sudo apt-get autoclean
```

again?

---

### Post by SuperFreak on 2012-10-31
OK tried first solution I quoted and it didn't work. Error message prevented it from proceeding.

Then I tried ```
sudo apt-get remove libsane:i386
```

This was the output:
```
Package libsane:i386 is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libsane:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
 I then tried as you suggested:
```
sudo apt-get clean && sudo apt-get autoclean
```


and got this:
```
desktop:~$  sudo apt-get clean && sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by karlstad on 2012-10-31
Okay. Then maybe it will help to try and remove ia32-libs-multiarch:i386.

```
sudo apt-get remove ia32-libs-multiarch:i386
```

---

### Post by SuperFreak on 2012-10-31
Didn't work 

```
desktop:~$ sudo apt-get remove ia32-libs-multiarch:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
david@david-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following NEW packages will be installed:
  libsane:i386
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,554 kB of archives.
After this operation, 8,503 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 307692 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.22-7ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb (--unpack):
 './lib/udev/rules.d/40-libsane.rules' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by karlstad on 2012-10-31
Okay. Try adding ia32-libs to the list of packages to remove.

```
sudo apt-get remove ia32-libs ia32-libs-multiarch:i386
```

And see if that helps.. :)

---

### Post by squakie on 2012-10-31
You could try:

sudo apt-get build-dep ia32-libs

and then:

sudo apt-get build-dep ia32-libs-multiarch:i386

With the problems you are having it sounds like the apt cache is messed up, but the previous instructions I think should have taken care of it.  The 2 commands above tell apt to gather the dependencies for the given package.  I don't know if it's possible to add the -f (force) option with those or not.

---

### Post by SuperFreak on 2012-10-31
@ karlstad I applied ```
sudo apt-get remove ia32-libs ia32-libs-multiarch:i386
```

@squakie I applied
```
sudo apt-get build-dep ia32-libs

sudo apt-get build-dep ia32-libs-multiarch:i386

```


The update manger is no longer returning error messages which is good. I am hoping the matter is fixed now. Greatly appreciate the help you both gave me. I will mark it as SOLVED in a few days when I am sure everything is working properly

---

### Post by SuperFreak on 2012-10-31
I would have like to mark this as SOLVED but problems remain. I tried installing the free Crossover application offered today only through codeweavers but get error messages as follows :
```
(Reading database ... 307692 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.22-7ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb (--unpack):
 './lib/udev/rules.d/40-libsane.rules' is different from the same file on the system
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.22-7ubuntu1_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of ia32-libs-multiarch:i386:
 ia32-libs-multiarch:i386 depends on libsane; however:
  Package libsane:i386 is not installed.
dpkg: error processing ia32-libs-multiarch:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on ia32-libs-multiarch; however:
  Package ia32-libs-multiarch is not installed.
  Package ia32-libs-multiarch:i386 is not configured yet.
dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured


```

I don't care if I can't use Crossover greatly but now I am unable to update 12.04 again. Getting same error about Libsane. Very frustrating I hope I am not having to reinstall 12.04

---

### Post by squakie on 2012-10-31
use synaptic package manager (if you don't have it,  use the software center to get it).  Search there for "libsane" and report back the results.  It may be it is not installed.  However, there is another problem happening here.  Apparently the package is trying to install a new 40-libsane.rules file in the udev definitions.  The package manager is saying it is different from the one already on the system, and it is not replacing it.   This may be a problem with permissions when it gets to that point - I don't know.  If you are using apt-get for packages, I would strongly suggest using either the software center or better yet the synaptics package manager.  While they are supposed to be front-ends to apt, I have always had better "luck" using one of the package managers.  When you use one of those please post back and tell us the errors you get.

Also, are you running 32-bit (the default when you download the install CD image) or 64-bit Ubuntu?

---

### Post by jvill on 2012-11-01
I just found this thread and am having this same problem. When i run
     Code:
     sudo apt-get remove ia32-libs ia32-libs-multiarch:i386 
I get 
     Code:
     E: Unable to find a source package for ia32-libs-multiarch:i386 
I am  running the 64 bit Ubuntu.

---

### Post by HiImTye on 2012-11-01
it's complaining about an existing file, so try moving the file so that it isn't an issue anymore
```
sudo mv  /lib/udev/rules.d/40-libsane.rules /lib/udev/rules.d/40-libsane.rules~
```
repeat for any other files it complains about

---

### Post by squakie on 2012-11-01
I'm not one to totally understand, but I noticed "libsane_1.0.22-7ubuntu1_i386.deb" as the coming from the package, and I know it doesn't always apply, but when I see "i386" I think of 32-bit packages, not 64-bit packages.  Also, do you have any old repositories enabled, or all they all current with your release?  I'm curious because I'm running 12.10 and the version of libsane isn't 1.0.22-7 - it's much higher.  Have you somewhere in the past perhaps performed an upgrade from one release to another in place of a reinstall?

As mentioned above, deleting the udev rules file may work, but I'm curious if perhaps the one already installed is newer than the one it is trying to install - if so, I wouldn't delete the installed one but instead try to track down why you are picking up what appears to be an older version of libsane with an older version of the udev rules file.

---

### Post by squakie on 2012-11-01
If I remember correctly, there is a purge option to apt-get.  I would suggest:

sudo apt-get purge ia32-libs ia32-libs-mutiarch

- and -

sudo apt-get purge libsane

- then -

go back through synaptic and try installing libsane only and see what it says now.

---

### Post by SuperFreak on 2012-11-01
I am running Ubuntu 12.04 64 Bit with Cinnamon DE
I tried the purge commands and it said multi arch was not installed. Went ahead and purged Libsane and reinstalled. The images show before and after purge
Also a list of Repositories installed. Not sure how to tell if there is a suspect repository there, but I may well have something that doesn't belong there

---

### Post by SuperFreak on 2012-11-01
The last few changes (purge & reinstall of Libsane) may have , I hope, have fixed things. I tried to install Crossover again and it did not throw up error messages this time and Update Manager still appears to work without error. I will let you know if anything happens in the next day or so that indicates further problems and then mark it as solved

---

### Post by AlexDudko on 2012-11-01
It's a [bug]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294") and at this very moment there's no solution yet.
The error can be removed by manually by removing all packages for i386 architecture. But then there'll be no Skype, Google Earth and other programmes which need i386 libraries.

---

### Post by SuperFreak on 2012-11-01
So far the scanner wouldn't work. Reinstalling the driver fixed that though.
Out of curiosity I installed Google Earth. It doesn't run though as the previous poster said.

---

### Post by squakie on 2012-11-01
I'm glad the purges at least got you further.  Someone put me on to that a few years ago.

---

### Post by SuperFreak on 2012-11-01
Yes, and thanks again for your help. I think it made the difference between a reinstall of 12.04 or a working system which I now have. I hope the bug is fixed on 12.04.

---

