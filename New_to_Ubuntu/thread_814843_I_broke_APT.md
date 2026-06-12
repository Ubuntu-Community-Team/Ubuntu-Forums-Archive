---
title: "I broke APT"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by R.a.i.x on 2008-06-01
I am trying to update but it keeps failing with the following error
```
E: /var/cache/apt/archives/util-linux_2.13.1-5ubuntu1_i386.deb: failed to install updated files list file for package util-linux
```

Attempting to install or remove anything results in the same error.

Please help!

---

### Post by rraj.be on 2008-06-01
Open terminal and run 

```
dpkg --configure -a
```

this will clean all such errors with your package manager

---

### Post by rraj.be on 2008-06-01
Or just try to remove that specific utility from your system.

you cant do it sing PM.

but by following the steps below.

open terminal and type 

```
sudo -i
```

this will ask for your pasword.

Enter it.

type

```
rm /var/cache/apt/archives/util-linux_2.13.1-5ubuntu1_i386.deb
```

it will remove that utility package.

this might be resulted due to improper installation of that specific package.

be carefull when installing any thing.

---

### Post by R.a.i.x on 2008-06-01
I tried both of those suggestions to no effect.

On further notice alot more errors also appear
```
(Reading database ... 
dpkg: serious warning: files list file for package `libdjvulibre15' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gnome2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxplc0.3.13' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libvorbisfile3' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `kdebase-data' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwvstreams4.4-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `scrollkeeper' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mesa-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpolkit-dbus2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgtk-vnc-1.0-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `kdebase-bin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python2.5-minimal' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-input-wacom' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-ubuntu-modules-2.6.24-16-generic' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libbonobo2-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libebook1.2-9' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `cupsys-bsd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `rhythmbox' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-vesa' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpam-gnome-keyring' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `synaptic' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xinit' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gtk2-engines-pixbuf' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `guidance-backends' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libaudiofile0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `wget' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgl1-mesa-glx' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-problem-report' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxaw7' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgtksourceview2.0-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fortune-mod' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gtk2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libchromexvmcpro1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `pkg-config' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `tracker-search-tool' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-themes' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `pulseaudio-esound-compat' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iputils-tracepath' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libnautilus-extension1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `aspell' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fuse-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `pidgin-otr' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `w3m' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compizconfig-backend-gconf' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `util-linux' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-x' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `zip' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ca-certificates' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-tools' missing, assuming package has no files currently installed.
103433 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu1 (using .../util-linux_2.13.1-5ubuntu1_i386.deb) ...
Unpacking replacement util-linux ...
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu1_i386.deb (--unpack):
 failed to install updated files list file for package util-linux: Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am using Ubuntu 8.04 32-bit, installed from a ship-it CD.

I don't use this installation very often, and did not make alot of changes after installing it. My laptop - which also runs 8.04 does not have this problem and has updated successfully, my desktop fails with those messages.

Synaptic gives me a scary question dialog when I tell it to remove "util-linux" ```
Removing this package may render the system unusable.
Are you sure you want to do that?
```

Would trying to remove this package be a bad idea?

---

### Post by SunnyRabbiera on 2008-06-01
yeh dont remove anything you dont know about.
I personally suggest a restart to see what is going on.
This error is common in ubuntu, and sometimes a restart is best option if apt is hanging.

---

### Post by R.a.i.x on 2008-06-01
Rebooting solved the problem.

---

### Post by SunnyRabbiera on 2008-06-01
> **R.a.i.x said:**
> Rebooting solved the problem.

I thought so, sometimes apt can hang in the background. especially after a update, sometimes apt stays in the background even after a reboot...

---

### Post by rraj.be on 2008-06-01
I am extremely sorry.

I haven't mentioned to reinstall the package.

Really sorry dear.

I experienced the same problem a week ago and re instalation of that specific package solved my problem in 5 minutes.

so only i suggested that.

---

