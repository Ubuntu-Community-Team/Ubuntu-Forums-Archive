---
title: "Having trouble when installing new packages or trying a fresh install"
date: 2018-01-13
forum: New to Ubuntu
---

### Post by djburst1 on 2018-01-13
Hello all,
I get a lot of errors associated with packages and Grub commands. I've tried to do a fresh reinstall of ubuntu and even tried to install mint but both froze after hitting continue on the first install screen. Was hoping someone could help me out. I will try and include all the commands giving me trouble.

```
sudo apt-get upgrade
[sudo] password for dj: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I saw in another forum to run this command but I don't know what to make of it.
```
sudo ls -l /var/lib/dpkg
total 4624
drwxr-xr-x 2 root root    4096 Sep 17 21:04 alternatives
-rw-r--r-- 1 root root      11 Jul  9  2017 arch
-rw-r--r-- 1 root root  170080 Feb 15  2017 available
-rw-r--r-- 1 root root       8 Feb 15  2017 cmethopt
-rw-r--r-- 1 root root    1044 Jul  8  2017 diversions
-rw-r--r-- 1 root root    1079 Jul  8  2017 diversions-old
drwxr-xr-x 2 root root  425984 Jan 13 17:14 info
-rw-r----- 1 root root       0 Jan 13 17:14 lock
drwxr-xr-x 2 root root    4096 Jan 12  2016 parts
-rw-r--r-- 1 root root     228 Feb 15  2017 statoverride
-rw-r--r-- 1 root root 2045994 Jan 13 17:14 status
-rw-r--r-- 1 root root 2045971 Jan 13 17:07 status-old
drwxr-xr-x 2 root root    4096 Jan 13 17:14 triggers
drwxr-xr-x 2 root root    4096 Jan 13 17:14 updates

```

Also, Whenever the terminal states its creating a grub file it freezes on this line.
```
Found initrd image: /boot/initrd.img-4.8.0-36-generic
```

---

### Post by vasa1 on 2018-01-13
If you try to run some *apt-get* commands immediately after starting your computer, you may see responses such as```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```Usually, it means that the system is checking for updates itself and so you should just wait a while (5, 10, 15 min?) and then retry.

If you still have a problem, let people here know.

By the way, it's strongly recommended to _first_ run```
sudo apt-get update
```and _then_ to run```
sudo apt-get upgrade
```

From your first post, it's not clear that you have successfully installed *anything* as yet. Are those outputs from a live USB/DVD or from an actually installation on your hard drive?

---

### Post by djburst1 on 2018-01-13
This is from an actual installation. I made a partition on my macbook pro and installed Ubuntu on it.

Thanks for the tip on updating before upgrading, but even after waiting and running the update command I get the same error for the upgrade command.

Even with other commands this error is persistent. For example:
```

sudo apt-get install libncurses5-dev libncursesw5-dev
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by vasa1 on 2018-01-13
Please post the entire output of ```
sudo apt-get update && sudo apt-get upgrade
```after closing all other applications that may be using apt or apt-get.

To see that, post the output of```
ps axjf | grep apt
```On my system,```
$ ps axjf | grep apt
    1  2478   912   912 ?           -1 Sl       0   0:00 /usr/bin/python3 /usr/share/apt-xapian-index/update-apt-xapian-index-dbus
 3918  3934  3933  3918 pts/1     3933 S+    1001   0:00      \_ grep --color=auto apt
$ 
```

---

### Post by vasa1 on 2018-01-13
If you want to enter code tags by typing, please use [noparse]```
 and 
```, not <CODE> and </CODE>[/noparse]. Thanks.

---

### Post by djburst1 on 2018-01-13
I notice that my commands to try and reinstall ubuntu are listed. But I'm not sure what the last one is.

```
 ps axjf | grep apt
 1279  4186  4186  4155 ?           -1 S        0   0:00          \_ sudo apt-get install --reinstall ubuntu-desktop
 4186  4187  4186  4155 ?           -1 S        0   0:03          |   \_ apt-get install --reinstall ubuntu-desktop
 6271  6856  6855  6271 pts/18    6855 S+    1000   0:00                  \_ grep --color=auto apt

```

I realize that I haven't closed those processes, and am unsure how to. As expected my output for your first command gives the original error.
```
 sudo apt-get update && sudo apt-get upgrade
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                           
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                          
Hit:4 http://ppa.launchpad.net/adrozdoff/emacs/ubuntu xenial InRelease                                               
Hit:5 https://dl.winehq.org/wine-builds/ubuntu xenial InRelease                                                      
Ign:6 http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04 ./ InRelease                            
Hit:7 http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04 ./ Release                              
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                  
Hit:9 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease         
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [62.4 kB]      
Hit:11 http://ppa.launchpad.net/tails-team/tails-installer/ubuntu xenial InRelease                               
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]                    
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.1 kB]                           
Get:15 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]                    
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [85.1 kB]                       
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [233 kB]                           
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [185 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [268 kB]        
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]  
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4,712 B]
Fetched 1,575 kB in 1s (810 kB/s)                                                                 
Reading package lists... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by djburst1 on 2018-01-13
> If you want to enter code tags by typing, please use ```
 and 
```, not <CODE> and </CODE>. Thanks.
Ah Gotcha. Thanks!

---

### Post by vasa1 on 2018-01-13
Please try a full shutdown and reboot.

---

### Post by djburst1 on 2018-01-13
The reboot solved the lock issue! However, now I'm experiencing the other problem I originally mentioned.

This command gives an error.
```
sudo apt-get update && sudo apt-get upgrade
[sudo] password for dj: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:3 http://ppa.launchpad.net/adrozdoff/emacs/ubuntu xenial InRelease         
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Ign:5 http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04 ./ InRelease
Hit:6 http://download.opensuse.org/repositories/home:/strycore/xUbuntu_16.04 ./ Release
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Hit:8 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease    
Hit:10 https://dl.winehq.org/wine-builds/ubuntu xenial InRelease               
Hit:11 http://ppa.launchpad.net/tails-team/tails-installer/ubuntu xenial InRelease
Fetched 306 kB in 1s (270 kB/s)
Reading package lists... Done
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

And when I run the command it suggests the terminal gets frozen. I've waited ~6 minutes or so but nothing seems to happen.
```
sudo dpkg --configure -a
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.12) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.10.0-33-generic
Found linux image: /boot/vmlinuz-4.8.0-58-generic
Found initrd image: /boot/initrd.img-4.8.0-58-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic



```

---

### Post by vasa1 on 2018-01-13
You'll need to be patient until a GRUB/kernel expert comes around to help :)

What does```
sudo dpkg -C
```show?

---

### Post by djburst1 on 2018-01-13
No worries, I greatly appreciate the help I've received so far!  Thanks :D

---

### Post by djburst1 on 2018-01-13
> **vasa1 said:**
> What does```
sudo dpkg -C
```show?

Sure thing. This seems to be a long output.

```
sudo dpkg -C
[sudo] password for dj: 
Another process has locked the database for writing, and might currently be
modifying it, some of the following problems might just be due to that.

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 apport               automatically generate crash reports for debugging
 apport-gtk           GTK+ frontend for the apport crash report system
 binutils             GNU assembler, linker and binary utilities
 bluez-cups           Bluetooth printer driver for CUPS
 bluez-obexd          bluez obex daemon
 evince               Document (PostScript, PDF) viewer
 evince-common        Document (PostScript, PDF) viewer - common files
 firefox              Safe and easy web browser from Mozilla
 fwupdate             Tools to manage UEFI firmware updates
 fwupdate-signed      Linux Firmware Updater EFI signed binary
 gdb                  GNU Debugger
 gdbserver            GNU Debugger (remote server)
 gir1.2-packagekitglib-1.0 GObject introspection data for the PackageKit GLib l
 grub-efi-amd64-signed GRand Unified Bootloader, version 2 (EFI-AMD64 version, 
 grub-pc-bin          GRand Unified Bootloader, version 2 (PC/BIOS binaries)
 gvfs:amd64           userspace virtual filesystem - GIO module
 gvfs-backends        userspace virtual filesystem - backends
 gvfs-bin             userspace virtual filesystem - binaries
 gvfs-common          userspace virtual filesystem - common data files
 gvfs-daemons         userspace virtual filesystem - servers
 gvfs-fuse            userspace virtual filesystem - fuse server
 gvfs-libs:amd64      userspace virtual filesystem - private libraries
 imagemagick          image manipulation programs -- binaries
 imagemagick-6.q16    image manipulation programs -- quantum depth Q16
 libasn1-8-heimdal:amd64 Heimdal Kerberos - ASN.1 library
 libasn1-8-heimdal:i386 Heimdal Kerberos - ASN.1 library
 libbluetooth3:amd64  Library to use the BlueZ Linux Bluetooth stack
 libevdocument3-4:amd64 Document (PostScript, PDF) rendering library
 libevview3-3:amd64   Document (PostScript, PDF) rendering library - Gtk+ widge
 libfreerdp-cache1.1:amd64 Free Remote Desktop Protocol library (cache library)
 libfreerdp-client1.1:amd64 Free Remote Desktop Protocol library (client library)
 libfreerdp-codec1.1:amd64 Free Remote Desktop Protocol library (codec library)
 libfreerdp-common1.1.0:amd64 Free Remote Desktop Protocol library (common library)
 libfreerdp-core1.1:amd64 Free Remote Desktop Protocol library (core library)
 libfreerdp-crypto1.1:amd64 Free Remote Desktop Protocol library (freerdp-crypto libr
 libfreerdp-gdi1.1:amd64 Free Remote Desktop Protocol library (GDI library)
 libfreerdp-locale1.1:amd64 Free Remote Desktop Protocol library (locale library)
 libfreerdp-plugins-standard:amd64 RDP client for Windows Terminal Services (plugins)
 libfreerdp-primitives1.1:amd64 Free Remote Desktop Protocol library (primitives libr
 libfreerdp-utils1.1:amd64 Free Remote Desktop Protocol library (freerdp-utils libra
 libfwup0:amd64       Library to manage UEFI firmware updates
 libgd3:amd64         GD Graphics Library
 libgd3:i386          GD Graphics Library
 libgraphite2-3:amd64 Font rendering engine for Complex Scripts -- library
 libgraphite2-3:i386  Font rendering engine for Complex Scripts -- library
 libgssapi3-heimdal:amd64 Heimdal Kerberos - GSSAPI support library
 libgssapi3-heimdal:i386 Heimdal Kerberos - GSSAPI support library
 libhcrypto4-heimdal:amd64 Heimdal Kerberos - crypto library
 libhcrypto4-heimdal:i386 Heimdal Kerberos - crypto library
 libheimbase1-heimdal:amd64 Heimdal Kerberos - Base library
 libheimbase1-heimdal:i386 Heimdal Kerberos - Base library
 libheimntlm0-heimdal:amd64 Heimdal Kerberos - NTLM support library
 libheimntlm0-heimdal:i386 Heimdal Kerberos - NTLM support library
 libhx509-5-heimdal:amd64 Heimdal Kerberos - X509 support library
 libhx509-5-heimdal:i386 Heimdal Kerberos - X509 support library
 libinput-bin         input device management and event handling library - udev
 libinput10:amd64     input device management and event handling library - shar
 libkrb5-26-heimdal:amd64 Heimdal Kerberos - libraries
 libkrb5-26-heimdal:i386 Heimdal Kerberos - libraries
 liblouis-data        Braille translation library - data
 liblouis9:amd64      Braille translation library - shared libs
 libmagickcore-6.q16-2-extra:amd64 low-level image manipulation library - extra codec
 libpackagekit-glib2-16:amd64 Library for accessing PackageKit using GLib
 libroken18-heimdal:amd64 Heimdal Kerberos - roken support library
 libroken18-heimdal:i386 Heimdal Kerberos - roken support library
 libsnapd-glib1:amd64 GLib snapd library
 libunity-control-center1 utilities to configure the GNOME desktop
 libwacom-bin         Wacom model feature query library -- binaries
 libwayland-cursor0:amd64 wayland compositor infrastructure - cursor library
 libwayland-cursor0:i386 wayland compositor infrastructure - cursor library
 libwind0-heimdal:amd64 Heimdal Kerberos - stringprep implementation
 libwind0-heimdal:i386 Heimdal Kerberos - stringprep implementation
 libwinpr-crt0.1:amd64 Windows Portable Runtime library (crt library)
 libwinpr-dsparse0.1:amd64 Windows Portable Runtime library (dsparse library)
 libwinpr-environment0.1:amd64 Windows Portable Runtime library (environment library)
 libwinpr-file0.1:amd64 Windows Portable Runtime library (file library)
 libwinpr-handle0.1:amd64 Windows Portable Runtime library (handle library)
 libwinpr-heap0.1:amd64 Windows Portable Runtime library (heap library)
 libwinpr-library0.1:amd64 Windows Portable Runtime library (library)
 libwinpr-path0.1:amd64 Windows Portable Runtime library (path library)
 libwinpr-pool0.1:amd64 Windows Portable Runtime library (pool library)
 libwinpr-registry0.1:amd64 Windows Portable Runtime library (registry library)
 libwinpr-rpc0.1:amd64 Windows Portable Runtime library (RPC library)
 libwinpr-sspi0.1:amd64 Windows Portable Runtime library (sspi library)
 libwinpr-synch0.1:amd64 Windows Portable Runtime library (synch library)
 libwinpr-sysinfo0.1:amd64 Windows Portable Runtime library (sysinfo library)
 libwinpr-thread0.1:amd64 Windows Portable Runtime library (thread library)
 libwinpr-utils0.1:amd64 Windows Portable Runtime library (utils library)
 libxfont1:amd64      X11 font rasterisation library
 linux-firmware       Firmware for Linux kernel drivers
 linux-generic-hwe-16.04 Complete Generic Linux kernel and headers
 linux-headers-4.10.0-33 Header files related to Linux kernel version 4.10.0
 linux-headers-4.10.0-33-generic Linux kernel headers for version 4.10.0 on 64 
 linux-headers-generic-hwe-16.04 Generic Linux kernel headers
 linux-image-4.10.0-33-generic Linux kernel image for version 4.10.0 on 64 bit 
 linux-image-extra-4.10.0-33-generic Linux kernel extra modules for version 4.1
 linux-image-generic-hwe-16.04 Generic Linux kernel image
 linux-libc-dev:amd64 Linux Kernel Headers for development
 linux-signed-generic-hwe-16.04 Complete Signed Generic Linux kernel and header
 linux-signed-image-4.10.0-33-generic Signed kernel image generic
 linux-signed-image-generic-hwe-16.04 Signed Generic Linux kernel image
 logrotate            Log rotation utility
 lutris               Install and play any video game easily
 mesa-vdpau-drivers:amd64 Mesa VDPAU video acceleration drivers
 mesa-vdpau-drivers:i386 Mesa VDPAU video acceleration drivers
 python3-apport       Python 3 library for Apport crash report handling
 python3-distupgrade  manage release upgrades
 python3-jwt          Python 3 implementation of JSON Web Token
 python3-louis        Python bindings for liblouis
 python3-problem-report Python 3 library to handle problem reports
 python3-update-manager python 3.x module for update-manager
 session-shortcuts    Allows you to shutdown, logout, and reboot from dash
 shim-signed          Secure Boot chain-loading bootloader (Microsoft-signed bi
 shotwell             digital photo organizer
 shotwell-common      digital photo organizer - common files
 snapd-login-service  Daemon to allow non-root access to snapd
 sudo                 Provide limited super user privileges to specific users
 tcpdump              command-line network traffic analyzer
 thunderbird          Email, RSS and newsgroup client with integrated spam filt
 thunderbird-gnome-support Email, RSS and newsgroup client - GNOME support
 thunderbird-locale-en English language pack for Thunderbird
 thunderbird-locale-en-us Transitional English language pack for Thunderbird
 ubuntu-desktop       The Ubuntu desktop system
 ubuntu-release-upgrader-core manage release upgrades
 ubuntu-release-upgrader-gtk manage release upgrades
 unattended-upgrades  automatic installation of security upgrades
 unity-control-center utilities to configure the GNOME desktop
 unity-control-center-faces utilities to configure the GNOME desktop - faces im
 update-manager       GNOME application that manages apt updates
 update-manager-core  manage release upgrades
 update-notifier      Daemon which notifies about package updates
 update-notifier-common Files shared between update-notifier and other packages
 woeusb               WoeUSB can create bootable windows installer on usb.
 xfonts-utils         X Window System font utility programs
 xserver-xorg-input-all-hwe-16.04 X.Org X server -- input driver metapackage
 xserver-xorg-legacy-hwe-16.04 setuid root Xorg server wrapper
 xserver-xorg-video-all-hwe-16.04 X.Org X server -- output driver metapackage

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 grub-efi-amd64       GRand Unified Bootloader, version 2 (EFI-AMD64 version)

The following packages have been triggered, but the trigger processing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 dbus                 simple interprocess messaging system (daemon and utilitie
 initramfs-tools      generic modular initramfs generator (automation)
 libc-bin             GNU C Library: Binaries


```

---

### Post by vasa1 on 2018-01-13
Wow!

Could you take a step back and describe what you did, right from the start, when you decided to install Ubuntu?

This bit isn't clear:> I've tried to do a fresh reinstall of ubuntu and even tried to install mint but both froze after hitting continue on the first install screen.So how did you get from there to where you are now?

---

### Post by djburst1 on 2018-01-13
I've had Ubuntu for about 4 months on my partition. I've installed a lot of different programs and such over that time ranging from gaming to programming libraries and have always just copy pasted the commands given to me into the terminal. Over time less and less things I've tried to install have been successful and brings me to where I'm at today. I've seen numerous different errors and infinite solutions from various message boards full of commands that were a foreign language to me.

Today, I was super frustrated with the errors I was receiving that I just tried to boot from the installation disk and reinstall Ubuntu, but after I hit continue on the first screen my cursor changes to the loading and nothing happens (I've waited for ~20 minutes or so). I decided to try the re installation with Mint only to have it do the same exact thing. #-o

---

### Post by vasa1 on 2018-01-13
> **djburst1 said:**
> I've had Ubuntu for about 4 months on my partition. I've installed a lot of different programs and such over that time ranging from gaming to programming libraries and have always just copy pasted the commands given to me into the terminal. Over time less and less things I've tried to install have been successful and brings me to where I'm at today. I've seen numerous different errors and infinite solutions from various message boards full of commands that were a foreign language to me.

Today, I was super frustrated with the errors I was receiving that I just tried to boot from the installation disk and reinstall Ubuntu, but after I hit continue on the first screen my cursor changes to the loading and nothing happens (I've waited for ~20 minutes or so). I decided to try the re installation with Mint only to have it do the same exact thing. #-o

Re. Mint, you may prefer to ask at [https://forums.linuxmint.com](https://forums.linuxmint.com).

Re. *I've installed a lot of different programs and such over that time ranging from gaming to programming libraries and have always just copy pasted the commands given to me into the terminal*, adding software from outside the standard repos may lead to problems :(

Re. the "installtion disk", from where did you get it? Did you check its integrity?

---

### Post by djburst1 on 2018-01-13
> **vasa1 said:**
> 
Re. the "installtion disk", from where did you get it? Did you check its integrity?

I downloaded the iso from one of the mirrors on ubuntu.com/downloads and created a bootable usb. Do you think I just didn't wait long enough after clicking continue? I don't remember my first installation taking that long on that screen.

Is there a way to just start Ubuntu from scratch? Is there a restore/reinstall completely function? I figured that booting from the bootable usb I made like the first time I installed would do just that but I could be mistaken.

---

### Post by vasa1 on 2018-01-13
> **djburst1 said:**
> I downloaded the iso from one of the mirrors on ubuntu.com/downloads and created a bootable usb. Do you think I just didn't wait long enough after clicking continue? I don't remember my first installation taking that long on that screen.

Is there a way to just start Ubuntu from scratch? Is there a restore/reinstall completely function? I figured that booting from the bootable usb I made like the first time I installed would do just that but I could be mistaken.

Whenever you download an iso, you should also look at [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu).

And, no, you shouldn't have to wait long in the initial steps. The time taken for actual installation of software may depend on your net speed and computer specs.

---

### Post by djburst1 on 2018-01-14
I just noticed that I installed the 64-bit version of Ubuntu, but I have an Intel processor on my Macbook. Isn't that not compatible? I just read on your 'verify Ubuntu' link that you should use the 32 bit version if your machine doesn't have an AMD processor. Could this be the reason for my issues? :shock::idea:

---

### Post by deadflowr on 2018-01-14
> **djburst1 said:**
> I just noticed that I installed the 64-bit version of Ubuntu, but I have an Intel processor on my Macbook. Isn't that not compatible? I just read on your 'verify Ubuntu' link that you should use the 32 bit version if your machine doesn't have an AMD processor. Could this be the reason for my issues? :shock::idea:

No.
Intel processors are perfectly fine to run with 64-bit Ubuntu.
Where did it even say that?

If the machine had an incompatible cpu then it would never run at all.

---

### Post by vasa1 on 2018-01-14
> **djburst1 said:**
> I just noticed that I installed the 64-bit version of Ubuntu, but I have an Intel processor on my Macbook. Isn't that not compatible? I just read on your 'verify Ubuntu' link that you should use the 32 bit version if your machine doesn't have an AMD processor. Could this be the reason for my issues? :shock::idea:

See [https://unix.stackexchange.com/questions/53415/why-are-64-bit-distros-often-called-amd64](https://unix.stackexchange.com/questions/53415/why-are-64-bit-distros-often-called-amd64)

Just to be sure, post the output of```
lscpu
```

---

