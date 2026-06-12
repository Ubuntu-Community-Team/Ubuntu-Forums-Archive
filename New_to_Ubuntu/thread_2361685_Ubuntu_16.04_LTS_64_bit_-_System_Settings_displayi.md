---
title: "Ubuntu 16.04 LTS 64 bit - System Settings displaying 'phone' settings window"
date: 2017-05-19
forum: New to Ubuntu
---

### Post by ian1971 on 2017-05-19
Hi,

I've noticed recently that System Settings is displaying a 'phone' version of the settings window when I'm using Ubuntu on desktop.  For example, I can see options for Rotation Lock and Flight Mode.  Does anyone know how to reset this back to the desktop version?  If this is of any additional help, I use the Numix Circles icon set, but the System Settings icon is displaying the original Unity icon.

Thanks for any help.

---

### Post by deadflowr on 2017-05-19
That's actually the settings for unity8.
You should check if you have another settings in the dash search menu.

(Or see if it opens from the top panel; the cog-like icon at the far right of the top panel should have a system settings section from it's dropdown menu;; if that make sense)

---

### Post by ian1971 on 2017-05-19
Thanks for the quick reply.

There are no other 'settings' options in the dash menu and when trying to open System Settings via the top right icon nothing appears to happen.

---

### Post by deadflowr on 2017-05-19
Hmm,
system settings is really a program called unity-control-center.
so you can try opening a terminal program and run
```
unity-control-center
```
what happens there?

---

### Post by ian1971 on 2017-05-19
I get the following:
The program 'unity-control-center' is currently not installed. You can install it by typing:
sudo apt install unity-control-center

---

### Post by ian1971 on 2017-05-19
When running 'sudo apt install unity-control-center', I receive the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 unity-control-center : Depends: libcheese-gtk25 (>= 3.18.0) but it is not going to be installed
                        Depends: libcheese8 (>= 3.18.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by deadflowr on 2017-05-19
See what these output
```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by ian1971 on 2017-05-19
sudo apt update:

```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:3 [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) xenial InRelease          
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:5 [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) xenial InRelease         
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:7 [http://ppa.launchpad.net/numix/ppa/ubuntu](http://ppa.launchpad.net/numix/ppa/ubuntu) xenial InRelease               
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]    
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [540 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [54.7 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [50.3 kB]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [525 kB]
Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [298 kB]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [193 kB]
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [468 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [453 kB]
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [159 kB]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [7,996 B]
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [3,980 B]
Fetched 3,323 kB in 1s (2,014 kB/s)                                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
14 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

sudo apt upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  cheese-common gstreamer0.10-gconf gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-clutter libcdaudio1
  libclutter-gst-2.0-0 libenca0 libfaac0 libgnome-desktop-3-7 libgtop2-7
  libslv2-9 libtimezonemap-data libtimezonemap1 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-headers-4.4.0-42
  linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-headers-4.4.0-45
  linux-headers-4.4.0-45-generic linux-headers-4.4.0-47
  linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-67
  linux-headers-4.4.0-67-generic linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
  linux-headers-4.4.0-72-generic linux-headers-4.4.0-75
  linux-headers-4.4.0-75-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-43-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-47-generic linux-image-4.4.0-51-generic
  linux-image-4.4.0-53-generic linux-image-4.4.0-57-generic
  linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic
  linux-image-4.4.0-63-generic linux-image-4.4.0-64-generic
  linux-image-4.4.0-66-generic linux-image-4.4.0-67-generic
  linux-image-4.4.0-71-generic linux-image-4.4.0-72-generic
  linux-image-4.4.0-75-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-43-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-47-generic linux-image-extra-4.4.0-51-generic
  linux-image-extra-4.4.0-53-generic linux-image-extra-4.4.0-57-generic
  linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic
  linux-image-extra-4.4.0-63-generic linux-image-extra-4.4.0-64-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-67-generic
  linux-image-extra-4.4.0-71-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-75-generic linux-signed-image-4.4.0-31-generic
  linux-signed-image-4.4.0-34-generic linux-signed-image-4.4.0-36-generic
  linux-signed-image-4.4.0-38-generic linux-signed-image-4.4.0-42-generic
  linux-signed-image-4.4.0-43-generic linux-signed-image-4.4.0-45-generic
  linux-signed-image-4.4.0-47-generic linux-signed-image-4.4.0-51-generic
  linux-signed-image-4.4.0-53-generic linux-signed-image-4.4.0-57-generic
  linux-signed-image-4.4.0-59-generic linux-signed-image-4.4.0-62-generic
  linux-signed-image-4.4.0-63-generic linux-signed-image-4.4.0-64-generic
  linux-signed-image-4.4.0-66-generic linux-signed-image-4.4.0-67-generic
  linux-signed-image-4.4.0-71-generic linux-signed-image-4.4.0-72-generic
  linux-signed-image-4.4.0-75-generic linux-tools-4.4.0-31
  linux-tools-4.4.0-31-generic linux-tools-4.4.0-34
  linux-tools-4.4.0-34-generic linux-tools-4.4.0-36
  linux-tools-4.4.0-36-generic linux-tools-4.4.0-38
  linux-tools-4.4.0-38-generic linux-tools-4.4.0-42
  linux-tools-4.4.0-42-generic linux-tools-4.4.0-43
  linux-tools-4.4.0-43-generic linux-tools-4.4.0-45
  linux-tools-4.4.0-45-generic linux-tools-4.4.0-47
  linux-tools-4.4.0-47-generic linux-tools-4.4.0-51
  linux-tools-4.4.0-51-generic linux-tools-4.4.0-53
  linux-tools-4.4.0-53-generic linux-tools-4.4.0-57
  linux-tools-4.4.0-57-generic linux-tools-4.4.0-59
  linux-tools-4.4.0-59-generic linux-tools-4.4.0-62
  linux-tools-4.4.0-62-generic linux-tools-4.4.0-63
  linux-tools-4.4.0-63-generic linux-tools-4.4.0-64
  linux-tools-4.4.0-64-generic linux-tools-4.4.0-66
  linux-tools-4.4.0-66-generic linux-tools-4.4.0-67
  linux-tools-4.4.0-67-generic linux-tools-4.4.0-71
  linux-tools-4.4.0-71-generic linux-tools-4.4.0-72
  linux-tools-4.4.0-72-generic linux-tools-4.4.0-75
  linux-tools-4.4.0-75-generic mokutil shim snap-confine ubuntu-core-launcher
  ubuntu-system-service unity-control-center-faces
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  cjs gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gstreamer1.0-clutter libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0
The following packages will be upgraded:
  gnome-software gnome-software-common iproute2 numix-icon-theme
  ubuntu-software unattended-upgrades
6 to upgrade, 0 to newly install, 0 to remove and 8 not to upgrade.
Need to get 5,230 kB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 iproute2 amd64 4.3.0-1ubuntu3.16.04.1 [522 kB]
Get:2 [http://ppa.launchpad.net/numix/ppa/ubuntu](http://ppa.launchpad.net/numix/ppa/ubuntu) xenial/main amd64 numix-icon-theme all 0.3+898~201705182216~ubuntu16.04.1 [2,176 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ubuntu-software amd64 3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1 [11.7 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gnome-software amd64 3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1 [231 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gnome-software-common all 3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1 [2,257 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 unattended-upgrades all 0.90ubuntu0.6 [32.9 kB]
Fetched 5,230 kB in 4s (1,300 kB/s)                                            
Preconfiguring packages ...
(Reading database ... 942930 files and directories currently installed.)
Preparing to unpack .../iproute2_4.3.0-1ubuntu3.16.04.1_amd64.deb ...
Unpacking iproute2 (4.3.0-1ubuntu3.16.04.1) over (4.3.0-1ubuntu3) ...
Preparing to unpack .../ubuntu-software_3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1_amd64.deb ...
Unpacking ubuntu-software (3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1) over (3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1) ...
Preparing to unpack .../gnome-software_3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1_amd64.deb ...
Unpacking gnome-software (3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1) over (3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1) ...
Preparing to unpack .../gnome-software-common_3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1_all.deb ...
Unpacking gnome-software-common (3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1) over (3.20.1+git20170208.0.a34b091-0ubuntu1~xenial1) ...
Preparing to unpack .../unattended-upgrades_0.90ubuntu0.6_all.deb ...
Unpacking unattended-upgrades (0.90ubuntu0.6) over (0.90ubuntu0.5) ...
Preparing to unpack .../numix-icon-theme_0.3+898~201705182216~ubuntu16.04.1_all.deb ...
Unpacking numix-icon-theme (0.3+898~201705182216~ubuntu16.04.1) over (0.3+896~201705172217~ubuntu16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up iproute2 (4.3.0-1ubuntu3.16.04.1) ...
Setting up gnome-software-common (3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1) ...
Setting up gnome-software (3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1) ...
Setting up ubuntu-software (3.20.1+git20170427.0.3d09239-0ubuntu1~xenial1) ...
Setting up unattended-upgrades (0.90ubuntu0.6) ...
Replacing config file /etc/apt/apt.conf.d/50unattended-upgrades with new version
Setting up numix-icon-theme (0.3+898~201705182216~ubuntu16.04.1) ...
gtk-update-icon-cache: Cache file created successfully.
```

---

### Post by deadflowr on 2017-05-20
Hmm,
t's like the chicken and the egg.
Which to do first, remove the old removal packages, or try to make it install the packages that have been held back?
As it seems you need those new packages to satisfy what's needed to fix the current issue.
(The settings package needs cheese which need libcheese-gtk25 which in turn needs the libclutter package(s), et cetra)
What happens when you run
```
sudo apt full-upgrade
```

---

### Post by ian1971 on 2017-05-20
Thanks for the reply.  When I run the command, I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  cheese-common gstreamer0.10-gconf gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gstreamer1.0-clutter libcdaudio1
  libclutter-gst-2.0-0 libenca0 libfaac0 libgnome-desktop-3-7 libgtop2-7
  libslv2-9 libtimezonemap-data libtimezonemap1 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-headers-4.4.0-42
  linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-headers-4.4.0-45
  linux-headers-4.4.0-45-generic linux-headers-4.4.0-47
  linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-67
  linux-headers-4.4.0-67-generic linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
  linux-headers-4.4.0-72-generic linux-headers-4.4.0-75
  linux-headers-4.4.0-75-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-43-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-47-generic linux-image-4.4.0-51-generic
  linux-image-4.4.0-53-generic linux-image-4.4.0-57-generic
  linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic
  linux-image-4.4.0-63-generic linux-image-4.4.0-64-generic
  linux-image-4.4.0-66-generic linux-image-4.4.0-67-generic
  linux-image-4.4.0-71-generic linux-image-4.4.0-72-generic
  linux-image-4.4.0-75-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-43-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-47-generic linux-image-extra-4.4.0-51-generic
  linux-image-extra-4.4.0-53-generic linux-image-extra-4.4.0-57-generic
  linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic
  linux-image-extra-4.4.0-63-generic linux-image-extra-4.4.0-64-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-67-generic
  linux-image-extra-4.4.0-71-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-75-generic linux-signed-image-4.4.0-31-generic
  linux-signed-image-4.4.0-34-generic linux-signed-image-4.4.0-36-generic
  linux-signed-image-4.4.0-38-generic linux-signed-image-4.4.0-42-generic
  linux-signed-image-4.4.0-43-generic linux-signed-image-4.4.0-45-generic
  linux-signed-image-4.4.0-47-generic linux-signed-image-4.4.0-51-generic
  linux-signed-image-4.4.0-53-generic linux-signed-image-4.4.0-57-generic
  linux-signed-image-4.4.0-59-generic linux-signed-image-4.4.0-62-generic
  linux-signed-image-4.4.0-63-generic linux-signed-image-4.4.0-64-generic
  linux-signed-image-4.4.0-66-generic linux-signed-image-4.4.0-67-generic
  linux-signed-image-4.4.0-71-generic linux-signed-image-4.4.0-72-generic
  linux-signed-image-4.4.0-75-generic linux-tools-4.4.0-31
  linux-tools-4.4.0-31-generic linux-tools-4.4.0-34
  linux-tools-4.4.0-34-generic linux-tools-4.4.0-36
  linux-tools-4.4.0-36-generic linux-tools-4.4.0-38
  linux-tools-4.4.0-38-generic linux-tools-4.4.0-42
  linux-tools-4.4.0-42-generic linux-tools-4.4.0-43
  linux-tools-4.4.0-43-generic linux-tools-4.4.0-45
  linux-tools-4.4.0-45-generic linux-tools-4.4.0-47
  linux-tools-4.4.0-47-generic linux-tools-4.4.0-51
  linux-tools-4.4.0-51-generic linux-tools-4.4.0-53
  linux-tools-4.4.0-53-generic linux-tools-4.4.0-57
  linux-tools-4.4.0-57-generic linux-tools-4.4.0-59
  linux-tools-4.4.0-59-generic linux-tools-4.4.0-62
  linux-tools-4.4.0-62-generic linux-tools-4.4.0-63
  linux-tools-4.4.0-63-generic linux-tools-4.4.0-64
  linux-tools-4.4.0-64-generic linux-tools-4.4.0-66
  linux-tools-4.4.0-66-generic linux-tools-4.4.0-67
  linux-tools-4.4.0-67-generic linux-tools-4.4.0-71
  linux-tools-4.4.0-71-generic linux-tools-4.4.0-72
  linux-tools-4.4.0-72-generic linux-tools-4.4.0-75
  linux-tools-4.4.0-75-generic mokutil shim snap-confine ubuntu-core-launcher
  ubuntu-system-service unity-control-center-faces
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  cjs gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gstreamer1.0-clutter libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0
0 to upgrade, 0 to newly install, 0 to remove and 8 not to upgrade.
```

---

### Post by deadflowr on 2017-05-20
You might need to run
```
sudo apt autoremove
```
which will remove those old and removal packages that keep showing up.
it'll take a while to run since it'll need to remove all those old kernels.
after it does, re-try the upgrade commands again.

---

### Post by ian1971 on 2017-05-20
I've run those commands and restarted the computer, but the problem persists...

---

### Post by deadflowr on 2017-05-20
can you now install unity-control-center?
(Or did you try that again?)

---

### Post by ian1971 on 2017-05-20
No, I just ran the upgrade.  However, when I run:

sudo apt install unity-control-center

I receive the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 unity-control-center : Depends: libcheese-gtk25 (>= 3.18.0) but it is not going to be installed
                        Depends: libcheese8 (>= 3.18.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by deadflowr on 2017-05-20
> E: Unable to correct problems, you have held broken packages.
try the fix broken packages command
```
sudo apt-get install -f
```

---

### Post by ian1971 on 2017-05-20
This is the result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.

Should I try and install unity-control-center again?

---

### Post by deadflowr on 2017-05-20
> Should I try and install unity-control-center again?
No
You need to figure out why those 6 packages are being held back.

Did you at any point install packages outside the archives? from some website maybe?
Or did you at one point have other sources enabled, like from a ppa.

---

### Post by ian1971 on 2017-05-20
No, not that I'm aware of.  I'm a very 'light' user of Ubuntu and only accept the regular updates.  I have very little installed beyond that bundled with the original installation.

This issue isn't that big a deal, I can certainly continue to use the system without System Settings functioning correctly (I only noticed it by accident yesterday, so it may have been in this state for a long time).

Thanks for your help.

---

### Post by mc4man on 2017-05-20
Try to install libcheese8, i.e,
sudo apt install libcheese8

If apt isn't helpful as to why it can't be installed then install aptitude & try again
sudo apt install aptitude
sudo aptitude install libcheese8

aptitude should provide more info, if it offers solutions then decline (n or q) and post complete terminal output

---

### Post by ian1971 on 2017-05-21
Hi,

I've performed the tasks and suggested and received the following output:

The following NEW packages will be installed:
  libcheese8 libclutter-gst-3.0-0{a} libcogl-pango20{a} libcogl-path20{a} 
  libcogl20{ab} 
The following packages will be upgraded:
  libclutter-1.0-0 
1 packages upgraded, 5 newly installed, 0 to remove and 5 not upgraded.
Need to get 1,006 kB of archives. After unpacking 1,673 kB will be used.
The following packages have unmet dependencies:
 libcogl20 : Breaks: libcogl15 but 1.16.2-1 is installed.
The following actions will resolve these dependencies:


      Remove the following packages:
1)      caribou                     
2)      cinnamon                    
3)      gir1.2-clutter-1.0          
4)      gir1.2-cogl-1.0             
5)      gir1.2-coglpango-1.0        
6)      gir1.2-gtkclutter-1.0       
7)      gir1.2-muffin-3.0           
8)      libclutter-gtk-1.0-0        
9)      libcogl-pango15             
10)     libcogl15                   
11)     libmuffin0                  






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                       
1)      caribou                                            
2)      cinnamon                                           
3)      gir1.2-clutter-1.0                                 
4)      gir1.2-gtkclutter-1.0                              
5)      gir1.2-muffin-3.0                                  
6)      libclutter-1.0-0                                   
7)      libclutter-gtk-1.0-0                               
8)      libmuffin0                                         


      Keep the following packages at their current version:
9)      libcheese8 [Not Installed]                         
10)     libclutter-gst-3.0-0 [Not Installed]               
11)     libcogl-pango20 [Not Installed]                    
12)     libcogl-path20 [Not Installed]                     
13)     libcogl20 [Not Installed]                          






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                                     
1)      caribou                                                          
2)      cinnamon                                                         
3)      gir1.2-clutter-1.0                                               
4)      gir1.2-coglpango-1.0                                             
5)      gir1.2-gtkclutter-1.0                                            
6)      gir1.2-muffin-3.0                                                
7)      libcogl-pango15                                                  
8)      libcogl15                                                        
9)      libmuffin0                                                       


      Upgrade the following packages:                                    
10)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
11)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                                     
1)      caribou                                                          
2)      cinnamon                                                         
3)      gir1.2-clutter-1.0                                               
4)      gir1.2-cogl-1.0                                                  
5)      gir1.2-coglpango-1.0                                             
6)      gir1.2-gtkclutter-1.0                                            
7)      gir1.2-muffin-3.0                                                
8)      libcogl-pango15                                                  
9)      libcogl15                                                        
10)     libmuffin0                                                       


      Upgrade the following packages:                                    
11)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                         
1)      caribou                                              
2)      cinnamon                                             
3)      gir1.2-clutter-1.0                                   
4)      gir1.2-coglpango-1.0                                 
5)      gir1.2-gtkclutter-1.0                                
6)      gir1.2-muffin-3.0                                    
7)      libclutter-gtk-1.0-0                                 
8)      libcogl-pango15                                      
9)      libcogl15                                            
10)     libmuffin0                                           


      Upgrade the following packages:                        
11)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


     Remove the following packages:                              
1)     cinnamon                                                  
2)     gir1.2-gtkclutter-1.0                                     
3)     gir1.2-muffin-3.0                                         
4)     libclutter-gtk-1.0-0                                      
5)     libcogl-pango15                                           
6)     libcogl15                                                 
7)     libmuffin0                                                


     Upgrade the following packages:                             
8)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]     
9)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


     Remove the following packages:                                     
1)     cinnamon                                                         
2)     gir1.2-muffin-3.0                                                
3)     libcogl-pango15                                                  
4)     libcogl15                                                        
5)     libmuffin0                                                       


     Upgrade the following packages:                                    
6)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
7)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
8)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


     Keep the following packages at their current version:
1)     libcheese8 [Not Installed]                         
2)     libclutter-1.0-0 [1.16.4-0ubuntu2 (now)]           
3)     libclutter-gst-3.0-0 [Not Installed]               
4)     libcogl-pango20 [Not Installed]                    
5)     libcogl-path20 [Not Installed]                     
6)     libcogl20 [Not Installed]                          






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                                     
1)      cinnamon-bluetooth                                               
2)      cinnamon-translations                                            
3)      libcjs0e                                                         
4)      libcogl-pango15                                                  
5)      libcogl15                                                        
6)      libmozjs-24-0                                                    


      Install the following packages:                                    
7)      cinnamon-l10n [2.8.3-1 (xenial)]                                 
8)      gir1.2-gdesktopenums-3.0 [3.18.1-1ubuntu1 (xenial)]              
9)      gir1.2-gnomedesktop-3.0 [3.18.2-1ubuntu1 (xenial)]               
10)     gir1.2-meta-muffin-0.0 [2.8.4-1 (xenial)]                        
11)     gnome-backgrounds [3.18.0-1 (xenial)]                            
12)     javascript-common [11 (xenial)]                                  
13)     libcjs0 [2.8.0-1 (xenial)]                                       
14)     libjs-jquery [1.11.3+dfsg-4 (xenial)]                            
15)     libmozjs-24-0v5 [24.2.0-3ubuntu2 (xenial)]                       


      Upgrade the following packages:                                    
16)     cjs [2.8.0 (now) -> 2.8.0-1 (xenial)]                            
17)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
18)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
19)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


      Downgrade the following packages:                                  
20)     cinnamon [2.8.8 (now) -> 2.8.6-1ubuntu1 (xenial)]                
21)     cinnamon-common [2.8.8 (now) -> 2.8.6-1ubuntu1 (xenial)]         
22)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
23)     libnemo-extension1 [2.8.7 (now) -> 2.8.6-2 (xenial)]             
24)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  
25)     nemo [2.8.7 (now) -> 2.8.6-2 (xenial)]                           
26)     nemo-data [2.8.7 (now) -> 2.8.6-2 (xenial)]                      






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                                     
1)      cinnamon-bluetooth                                               
2)      cinnamon-translations                                            
3)      libcjs0e                                                         
4)      libcogl-pango15                                                  
5)      libcogl15                                                        
6)      libmozjs-24-0                                                    


      Install the following packages:                                    
7)      cinnamon-l10n [2.8.3-1 (xenial)]                                 
8)      gir1.2-gdesktopenums-3.0 [3.18.1-1ubuntu1 (xenial)]              
9)      gir1.2-gnomedesktop-3.0 [3.18.2-1ubuntu1 (xenial)]               
10)     gir1.2-meta-muffin-0.0 [2.8.4-1 (xenial)]                        
11)     gnome-backgrounds [3.18.0-1 (xenial)]                            
12)     libcjs0 [2.8.0-1 (xenial)]                                       
13)     libjs-jquery [1.11.3+dfsg-4 (xenial)]                            
14)     libmozjs-24-0v5 [24.2.0-3ubuntu2 (xenial)]                       


      Upgrade the following packages:                                    
15)     cjs [2.8.0 (now) -> 2.8.0-1 (xenial)]                            
16)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
17)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
18)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


      Downgrade the following packages:                                  
19)     cinnamon [2.8.8 (now) -> 2.8.6-1ubuntu1 (xenial)]                
20)     cinnamon-common [2.8.8 (now) -> 2.8.6-1ubuntu1 (xenial)]         
21)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
22)     libnemo-extension1 [2.8.7 (now) -> 2.8.6-2 (xenial)]             
23)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  
24)     nemo [2.8.7 (now) -> 2.8.6-2 (xenial)]                           
25)     nemo-data [2.8.7 (now) -> 2.8.6-2 (xenial)]                      


      Leave the following dependencies unresolved:                       
26)     libjs-jquery recommends javascript-common                        




Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                                     
1)      libcjs0e                                                         
2)      libcogl-pango15                                                  
3)      libcogl15                                                        
4)      libmozjs-24-0                                                    


      Install the following packages:                                    
5)      gir1.2-gdesktopenums-3.0 [3.18.1-1ubuntu1 (xenial)]              
6)      gir1.2-gnomedesktop-3.0 [3.18.2-1ubuntu1 (xenial)]               
7)      gir1.2-meta-muffin-0.0 [2.8.4-1 (xenial)]                        
8)      gnome-backgrounds [3.18.0-1 (xenial)]                            
9)      javascript-common [11 (xenial)]                                  
10)     libcjs0 [2.8.0-1 (xenial)]                                       
11)     libjs-jquery [1.11.3+dfsg-4 (xenial)]                            
12)     libmozjs-24-0v5 [24.2.0-3ubuntu2 (xenial)]                       


      Upgrade the following packages:                                    
13)     cjs [2.8.0 (now) -> 2.8.0-1 (xenial)]                            
14)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
15)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
16)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


      Downgrade the following packages:                                  
17)     cinnamon [2.8.8 (now) -> 2.8.6-1ubuntu1 (xenial)]                
18)     cinnamon-common [2.8.8 (now) -> 2.8.6-1ubuntu1 (xenial)]         
19)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
20)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  


      Leave the following dependencies unresolved:                       
21)     cinnamon recommends cinnamon-l10n                                




Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                                     
1)      caribou                                                          
2)      cinnamon                                                         
3)      gir1.2-clutter-1.0                                               
4)      gir1.2-coglpango-1.0                                             
5)      gir1.2-gtkclutter-1.0                                            
6)      gir1.2-muffin-3.0                                                
7)      libcogl-pango15                                                  
8)      libcogl15                                                        


      Upgrade the following packages:                                    
9)      gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
10)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


      Downgrade the following packages:                                  
11)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
12)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                                     
1)      caribou                                                          
2)      cinnamon                                                         
3)      gir1.2-clutter-1.0                                               
4)      gir1.2-cogl-1.0                                                  
5)      gir1.2-coglpango-1.0                                             
6)      gir1.2-gtkclutter-1.0                                            
7)      gir1.2-muffin-3.0                                                
8)      libcogl-pango15                                                  
9)      libcogl15                                                        


      Upgrade the following packages:                                    
10)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


      Downgrade the following packages:                                  
11)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
12)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                         
1)      caribou                                              
2)      cinnamon                                             
3)      gir1.2-clutter-1.0                                   
4)      gir1.2-coglpango-1.0                                 
5)      gir1.2-gtkclutter-1.0                                
6)      gir1.2-muffin-3.0                                    
7)      libclutter-gtk-1.0-0                                 
8)      libcogl-pango15                                      
9)      libcogl15                                            


      Upgrade the following packages:                        
10)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]


      Downgrade the following packages:                      
11)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]         
12)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]      






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                   
1)      caribou                                        
2)      cinnamon                                       
3)      gir1.2-clutter-1.0                             
4)      gir1.2-cogl-1.0                                
5)      gir1.2-coglpango-1.0                           
6)      gir1.2-gtkclutter-1.0                          
7)      gir1.2-muffin-3.0                              
8)      libclutter-gtk-1.0-0                           
9)      libcogl-pango15                                
10)     libcogl15                                      


      Downgrade the following packages:                
11)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]   
12)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


      Remove the following packages:                                     
1)      libcjs0e                                                         
2)      libcogl-pango15                                                  
3)      libcogl15                                                        
4)      libmozjs-24-0                                                    


      Install the following packages:                                    
5)      gir1.2-gdesktopenums-3.0 [3.18.1-1ubuntu1 (xenial)]              
6)      gir1.2-gnomedesktop-3.0 [3.18.2-1ubuntu1 (xenial)]               
7)      gir1.2-meta-muffin-0.0 [2.8.4-1 (xenial)]                        
8)      gnome-backgrounds [3.18.0-1 (xenial)]                            
9)      libcjs0 [2.8.0-1 (xenial)]                                       
10)     libjs-jquery [1.11.3+dfsg-4 (xenial)]                            
11)     libmozjs-24-0v5 [24.2.0-3ubuntu2 (xenial)]                       


      Upgrade the following packages:                                    
12)     cjs [2.8.0 (now) -> 2.8.0-1 (xenial)]                            
13)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
14)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
15)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


      Downgrade the following packages:                                  
16)     cinnamon [2.8.8 (now) -> 2.8.6-1ubuntu1 (xenial)]                
17)     cinnamon-common [2.8.8 (now) -> 2.8.6-1ubuntu1 (xenial)]         
18)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
19)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  


      Leave the following dependencies unresolved:                       
20)     libjs-jquery recommends javascript-common                        
21)     cinnamon recommends cinnamon-l10n                                




Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


     Remove the following packages:                              
1)     cinnamon                                                  
2)     gir1.2-gtkclutter-1.0                                     
3)     libclutter-gtk-1.0-0                                      
4)     libcogl-pango15                                           
5)     libcogl15                                                 


     Upgrade the following packages:                             
6)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]     
7)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]


     Downgrade the following packages:                           
8)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]              
9)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]           






Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:


     Remove the following packages:                                     
1)     cinnamon                                                         
2)     libcogl-pango15                                                  
3)     libcogl15                                                        


     Upgrade the following packages:                                    
4)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
5)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
6)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


     Downgrade the following packages:                                  
7)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
8)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  






Accept this solution? [Y/n/q/?] n


*** No more solutions available ***


The following actions will resolve these dependencies:


     Remove the following packages:                                     
1)     cinnamon                                                         
2)     libcogl-pango15                                                  
3)     libcogl15                                                        


     Upgrade the following packages:                                    
4)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
5)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
6)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


     Downgrade the following packages:                                  
7)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
8)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  






Accept this solution? [Y/n/q/?] n


*** No more solutions available ***


The following actions will resolve these dependencies:


     Remove the following packages:                                     
1)     cinnamon                                                         
2)     libcogl-pango15                                                  
3)     libcogl15                                                        


     Upgrade the following packages:                                    
4)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
5)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
6)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


     Downgrade the following packages:                                  
7)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
8)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  






Accept this solution? [Y/n/q/?] n


*** No more solutions available ***


The following actions will resolve these dependencies:


     Remove the following packages:                                     
1)     cinnamon                                                         
2)     libcogl-pango15                                                  
3)     libcogl15                                                        


     Upgrade the following packages:                                    
4)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
5)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
6)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


     Downgrade the following packages:                                  
7)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
8)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  






Accept this solution? [Y/n/q/?] n


*** No more solutions available ***


The following actions will resolve these dependencies:


     Remove the following packages:                                     
1)     cinnamon                                                         
2)     libcogl-pango15                                                  
3)     libcogl15                                                        


     Upgrade the following packages:                                    
4)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
5)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
6)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


     Downgrade the following packages:                                  
7)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
8)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  






Accept this solution? [Y/n/q/?] n


*** No more solutions available ***


The following actions will resolve these dependencies:


     Remove the following packages:                                     
1)     cinnamon                                                         
2)     libcogl-pango15                                                  
3)     libcogl15                                                        


     Upgrade the following packages:                                    
4)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
5)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
6)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


     Downgrade the following packages:                                  
7)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
8)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]                  






Accept this solution? [Y/n/q/?] n


*** No more solutions available ***


The following actions will resolve these dependencies:


     Remove the following packages:                                     
1)     cinnamon                                                         
2)     libcogl-pango15                                                  
3)     libcogl15                                                        


     Upgrade the following packages:                                    
4)     gir1.2-cogl-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]            
5)     gir1.2-coglpango-1.0 [1.16.2-1 (now) -> 1.22.0-2 (xenial)]       
6)     libclutter-gtk-1.0-0 [1.4.4-3ubuntu2.2 (now) -> 1.6.6-1 (xenial)]


     Downgrade the following packages:                                  
7)     libmuffin0 [2.8.5 (now) -> 2.8.4-1 (xenial)]                     
8)     muffin-common [2.8.5 (now) -> 2.8.4-1 (xenial)]

---

### Post by mc4man on 2017-05-21
I would suspect you used a cinnamon ppa in the past that's installed packages for trusty (is this current install an upgrade from trusty?
This would likely show
```
apt-cache policy cinnamon libmuffin0
```

If that's the case then any of the options would be ok, the 1st. one would be best.. Then if you want cinnamon install packages meant for 16.04

---

### Post by ian1971 on 2017-05-21
That worked!

I did install Cinnamon whilst on 14 LTS, but it stopped working after upgrading to 16 LTS, so I abandoned it and reverted back to Unity.

I've just accepted the first option from aptitude when installing libcheese8 and then installed unity-control-center again and everything is working perfectly.

Thank you very much for all of your help, it is much appreciated.

---

### Post by mc4man on 2017-05-21
When doing an upgrade vs. a fresh install it's generally best to use ppa-purge on any ppa's one has used before starting the upgrade. This prevents any issues as sometimes ppa packages are higher than those in the new release's standard repos. When that happens they are left in place during the upgrade process & can (usually) cause issues.

---

