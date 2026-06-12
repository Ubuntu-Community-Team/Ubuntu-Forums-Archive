---
title: "Unable to install Epson printer driver"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by Randyman99 on 2014-12-11
Epson has their own printer driver for Linux either epson-inkjet-printer-201113w_1.0.2-1lsb3.2_i386.deb or epson-inkjet-printer-escpr_1.4.4-1lsb3.2_i386.deb. The installation instructions says "In order to install Epson Inkjet Printer Driver, you need to install the package of LSB 3.2 beforehand."


So I run


```
**sudo apt-get install lsb 3.2**

```

Without posting the long printout, it comes down to this at the end:


```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libantlr3c-antlrdbg-3.2-0 : Conflicts: libantlr3c-3.2-0
 libgfs-1.3-2 : Conflicts: libgfs-mpi-1.3-2 but 20110329-dfsg.2-1build2 is to be installed
 libgfs-mpi-1.3-2 : Conflicts: libgfs-1.3-2 but 20110329-dfsg.2-1build2 is to be installed
E: Unable to correct problems, you have held broken packages.

```

So I figure I need to get rid of the offending packages and install the ones that were so offended. I run:


```
**sudo apt-get remove libgfs-mpi-1.3-2**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libgfs-mpi-1.3-2' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 121 not upgraded.

```

Says it wasn't there to remove. Next:


```
**sudo apt-get remove libantlr3c-3.2-0**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libantlr3c-3.2-0' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 121 not upgraded.

```

Says it wasn't there to remove. Next:


```
**sudo apt-get remove libgfs-1.3-2**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libgfs-1.3-2' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 121 not upgraded.

```

Says it wasn't there to remove. Next, on to the installs:


```
**sudo apt-get install libantlr3c-antlrdbg-3.2-0**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libantlr3c-antlrdbg-3.2-0
0 upgraded, 1 newly installed, 0 to remove and 121 not upgraded.
Need to get 42.3 kB of archives.
After this operation, 166 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libantlr3c-antlrdbg-3.2-0 i386 3.2-2ubuntu1 [42.3 kB]
Fetched 42.3 kB in 0s (91.4 kB/s)              
Selecting previously unselected package libantlr3c-antlrdbg-3.2-0:i386.
(Reading database ... 219730 files and directories currently installed.)
Preparing to unpack .../libantlr3c-antlrdbg-3.2-0_3.2-2ubuntu1_i386.deb ...
Unpacking libantlr3c-antlrdbg-3.2-0:i386 (3.2-2ubuntu1) ...
Setting up libantlr3c-antlrdbg-3.2-0:i386 (3.2-2ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...

```Seemed to install it okay. Next:




```
**sudo apt-get install libgfs-1.3-2**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libgfs-1.3-2
0 upgraded, 1 newly installed, 0 to remove and 121 not upgraded.
Need to get 395 kB of archives.
After this operation, 1,623 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libgfs-1.3-2 i386 20110329-dfsg.2-1build2 [395 kB]
Fetched 395 kB in 1s (310 kB/s)       
Selecting previously unselected package libgfs-1.3-2.
(Reading database ... 219736 files and directories currently installed.)
Preparing to unpack .../libgfs-1.3-2_20110329-dfsg.2-1build2_i386.deb ...
Unpacking libgfs-1.3-2 (20110329-dfsg.2-1build2) ...
Setting up libgfs-1.3-2 (20110329-dfsg.2-1build2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...

```

Installed it OK. Next:


```
**sudo apt-get install libgfs-mpi-1.3-2**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms dkms libcr0 libcuda1-331-updates libhwloc-plugins libhwloc5
  libibverbs1 libopenmpi1.6 libtorque2 nvidia-331-updates
  nvidia-331-updates-uvm nvidia-libopencl1-331-updates
  nvidia-opencl-icd-331-updates nvidia-prime nvidia-settings
  screen-resolution-extra
Suggested packages:
  bumblebee blcr-dkms libhwloc-contrib-plugins
The following packages will be REMOVED:
  libgfs-1.3-2
The following NEW packages will be installed:
  bbswitch-dkms dkms libcr0 libcuda1-331-updates libgfs-mpi-1.3-2
  libhwloc-plugins libhwloc5 libibverbs1 libopenmpi1.6 libtorque2
  nvidia-331-updates nvidia-331-updates-uvm nvidia-libopencl1-331-updates
  nvidia-opencl-icd-331-updates nvidia-prime nvidia-settings
  screen-resolution-extra
0 upgraded, 17 newly installed, 1 to remove and 121 not upgraded.
Need to get 39.0 MB of archives.
After this operation, 170 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libhwloc5 i386 1.8-1ubuntu1 [76.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dkms all 2.2.0.3-1.1ubuntu5.14.04 [64.6 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libcr0 i386 0.8.5-2.1 [18.3 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/restricted libcuda1-331-updates i386 331.113-0ubuntu0.0.4 [4,155 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty/main libibverbs1 i386 1.1.7-1ubuntu1 [23.7 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libtorque2 i386 2.4.16+dfsg-1.3ubuntu1 [72.5 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libopenmpi1.6 i386 1.6.5-8 [1,342 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libgfs-mpi-1.3-2 i386 20110329-dfsg.2-1build2 [404 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-331-updates i386 331.113-0ubuntu0.0.4 [27.7 MB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-331-updates-uvm i386 331.113-0ubuntu0.0.4 [64.6 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-libopencl1-331-updates i386 331.113-0ubuntu0.0.4 [10.3 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-opencl-icd-331-updates i386 331.113-0ubuntu0.0.4 [4,195 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty/main bbswitch-dkms i386 0.7-2ubuntu1 [10.9 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty/main nvidia-prime i386 0.6.2 [11.2 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty/main screen-resolution-extra all 0.17.1 [11.4 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ trusty/main nvidia-settings i386 331.20-0ubuntu8 [767 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libhwloc-plugins i386 1.8-1ubuntu1 [11.4 kB]
Fetched 39.0 MB in 12s (3,192 kB/s)                                            
(Reading database ... 219743 files and directories currently installed.)
Removing libgfs-1.3-2 (20110329-dfsg.2-1build2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Selecting previously unselected package libhwloc5:i386.
(Reading database ... 219736 files and directories currently installed.)
Preparing to unpack .../libhwloc5_1.8-1ubuntu1_i386.deb ...
Unpacking libhwloc5:i386 (1.8-1ubuntu1) ...
Selecting previously unselected package dkms.
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04) ...
Selecting previously unselected package libcr0.
Preparing to unpack .../libcr0_0.8.5-2.1_i386.deb ...
Unpacking libcr0 (0.8.5-2.1) ...
Selecting previously unselected package libcuda1-331-updates.
Preparing to unpack .../libcuda1-331-updates_331.113-0ubuntu0.0.4_i386.deb ...
Unpacking libcuda1-331-updates (331.113-0ubuntu0.0.4) ...
Selecting previously unselected package libibverbs1.
Preparing to unpack .../libibverbs1_1.1.7-1ubuntu1_i386.deb ...
Unpacking libibverbs1 (1.1.7-1ubuntu1) ...
Selecting previously unselected package libtorque2.
Preparing to unpack .../libtorque2_2.4.16+dfsg-1.3ubuntu1_i386.deb ...
Unpacking libtorque2 (2.4.16+dfsg-1.3ubuntu1) ...
Selecting previously unselected package libopenmpi1.6.
Preparing to unpack .../libopenmpi1.6_1.6.5-8_i386.deb ...
Unpacking libopenmpi1.6 (1.6.5-8) ...
Selecting previously unselected package libgfs-mpi-1.3-2.
Preparing to unpack .../libgfs-mpi-1.3-2_20110329-dfsg.2-1build2_i386.deb ...
Unpacking libgfs-mpi-1.3-2 (20110329-dfsg.2-1build2) ...
Selecting previously unselected package nvidia-331-updates.
Preparing to unpack .../nvidia-331-updates_331.113-0ubuntu0.0.4_i386.deb ...
Unpacking nvidia-331-updates (331.113-0ubuntu0.0.4) ...
Selecting previously unselected package nvidia-331-updates-uvm.
Preparing to unpack .../nvidia-331-updates-uvm_331.113-0ubuntu0.0.4_i386.deb ...
Unpacking nvidia-331-updates-uvm (331.113-0ubuntu0.0.4) ...
Selecting previously unselected package nvidia-libopencl1-331-updates.
Preparing to unpack .../nvidia-libopencl1-331-updates_331.113-0ubuntu0.0.4_i386.deb ...
Unpacking nvidia-libopencl1-331-updates (331.113-0ubuntu0.0.4) ...
Selecting previously unselected package nvidia-opencl-icd-331-updates.
Preparing to unpack .../nvidia-opencl-icd-331-updates_331.113-0ubuntu0.0.4_i386.deb ...
Unpacking nvidia-opencl-icd-331-updates (331.113-0ubuntu0.0.4) ...
Selecting previously unselected package bbswitch-dkms.
Preparing to unpack .../bbswitch-dkms_0.7-2ubuntu1_i386.deb ...
Unpacking bbswitch-dkms (0.7-2ubuntu1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.6.2_i386.deb ...
Unpacking nvidia-prime (0.6.2) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_331.20-0ubuntu8_i386.deb ...
Unpacking nvidia-settings (331.20-0ubuntu8) ...
Selecting previously unselected package libhwloc-plugins.
Preparing to unpack .../libhwloc-plugins_1.8-1ubuntu1_i386.deb ...
Unpacking libhwloc-plugins (1.8-1ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libhwloc5:i386 (1.8-1ubuntu1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04) ...
Setting up libcr0 (0.8.5-2.1) ...
Setting up libcuda1-331-updates (331.113-0ubuntu0.0.4) ...
Setting up libibverbs1 (1.1.7-1ubuntu1) ...
Setting up libtorque2 (2.4.16+dfsg-1.3ubuntu1) ...
Setting up libopenmpi1.6 (1.6.5-8) ...
Setting up libgfs-mpi-1.3-2 (20110329-dfsg.2-1build2) ...
Setting up nvidia-331-updates (331.113-0ubuntu0.0.4) ...
update-alternatives: using /usr/lib/nvidia-331-updates/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-331-updates/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-331-updates/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/nvidia-331-updates/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-331-updates/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-331-updates
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Adding system user `nvidia-persistenced' (UID 116) ...
Adding new group `nvidia-persistenced' (GID 126) ...
Adding new user `nvidia-persistenced' (UID 116) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-331-updates-331.113 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-39-generic
Building for architecture i686
Building initial module for 3.13.0-39-generic
Done.


nvidia_331_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-39-generic/updates/dkms/


depmod......


DKMS: install completed.
Setting up bbswitch-dkms (0.7-2ubuntu1) ...
Loading new bbswitch-0.7 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-39-generic
Building initial module for 3.13.0-39-generic
Done.


bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-39-generic/updates/dkms/


depmod....


DKMS: install completed.
Setting up nvidia-prime (0.6.2) ...
nvidia-prime start/running, process 9874
Setting up screen-resolution-extra (0.17.1) ...
Setting up nvidia-settings (331.20-0ubuntu8) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up nvidia-331-updates-uvm (331.113-0ubuntu0.0.4) ...
Loading new nvidia-331-updates-uvm-331.113 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-39-generic
Building for architecture i686
Building initial module for 3.13.0-39-generic
Done.


nvidia-331-updates-uvm:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-39-generic/updates/dkms/


depmod....


DKMS: install completed.
Setting up nvidia-libopencl1-331-updates (331.113-0ubuntu0.0.4) ...
Setting up nvidia-opencl-icd-331-updates (331.113-0ubuntu0.0.4) ...
Setting up libhwloc-plugins (1.8-1ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-39-generic

```




Seemed to install okay. So now I should be good to go with installing the Epson drivers:


```
**sudo apt-get install ./epson-inkjet-printer-201113w_1.0.2-1lsb3.2_i386-1.deb**

```


It ran for several minutes with a stream of output lines, most of which ended with "... was not found." I'm not optimistic, but I go to CUPS anyway. It sees the printer, but the correct driver is not there. I install a driver for a different printer model that seemed to be the closest, but it doesn't work (spits out a bunch of blank pages). I go back to the terminal, and just for yucks, run 


```
**sudo apt-get install lsb 3.2**

```


And get the same error messages about broken packages.


I also ran


```
**sudo aptget install -f**
**sudo aptget autoremove**

```


But this didn't help the problem.
I seem to be running in circles without a solution, and a new printer I can't use.

I also tried running

```

**sudo apt-get remove lsb 3.2**

```


That basically removed everything. Ubuntu still worked, but not on all cylinders. I figured it was easier to restore from a 5 day old archive that try to undo whatever damage I did.

---

### Post by leunam12 on 2014-12-11
I don't think there should be a space between the b and the 3 in lsb 3.2; maybe a hyphen, underscore or no space at all. type

```
sudo apt-get install lsb
```

then press tab twice to display all the options or try installing via Synaptic.

---

### Post by sandyd on 2014-12-11
Its just
```

sudo apt-get install lsb
```
From the vague instructions on the epson site, you could probably just install lsb-core, though that might not be enough.

A useful tool to see if a package exists is to use [http://packages.ubuntu.com](http://packages.ubuntu.com) or
```

apt-cache show <packagename>

```
(without arrows)

---

### Post by Mike_Walsh on 2014-12-11
Hi, Randyman99.

Pardon me for saying this, but you seem to going about this the hard way...! If you download the afore-mentioned driver (it's the same one my Stylus SX218 uses, except I use the 64-bit version) to your downloads folder, simply double-click on it, and the Software Centre will install it for you. It will grab all of the required dependencies as it does so.

I have had absolutely no problems doing it this way.....and I have installed this same driver into many different distros over the last 7 months.

You will find that the 'escpr' driver has far more limited functionality than the other one. I would advise using the ' [COLOR=#000000] epson-inkjet-printer-201113w_1.0.2-1lsb3.2_i386.deb' version.[/COLOR]

After that, go to Settings>Printers, and add it in the usual way, by following the wizard.

I could of course use Synaptic, but I'm a lazy bugger... ;)

Regards,

Mike.

BTW: What model of Epson do you require this for? It would help to know, as there ARE other drivers available than just the generic ones.....Epson aren't very forthcoming with information for us Linux users, as they insist that they 'don't actually provide Linux drivers' (or so one of their customer service people told me, many months ago...!)

You will find that in many cases, their business-oriented 'WorkForce' series drivers do, in fact, provide far better functionality than the ones available in the Epson Download Center.....but you tend to have to hunt these out., if you're not in the business community.

I find the best place to track these down is [http://www.openprinting.org](http://www.openprinting.org) 

Hope that helps.

---

### Post by Randyman99 on 2014-12-12
Mike - thank you. I'm locked out of Ubuntu right now due to a problem mounting my root partition at boot. I might have to restore, but am trying some things first. I'm using Manjaro right now - there CUPS "forbids" me from adding new printers - I added myself to the lpadmin group, but still no go. I need to boot into WIndows XP to use it, where it works fine. My new printer's an Epson WP-4020, which is the bottom end of the Workforce Pro line. It is a more solid build than the standard Workforce line, and quiet. It doesn't have the all-in-one features, but I still have those on my old HP, minus the printing part. The one thing I don't like about it so far is that it doesn't do borderless prints. There's a little color shift to the yellow from my old HP. I'll try your suggestion as soon as I get back into Ubuntu. I can't think it was a hard as it was turning out to be for me. Thanks for the link. I'll check it out when I get back up with Ubuntu. Epson does have Linux drivers to download from their website, but with the disclaimer that they're not supported, so I can't ask them for help.

---

### Post by JeQhdMD on 2014-12-13
Holy Pete!  . . 100% agree with Mike that you're doing this the "hard way" . . . 

1.   When you get your system un-hosed, open Ubuntu Software Center (USC) & install "Synaptic" (if not already installed),
2.  Find and install "gdebi" package manager . . . this is a useful compliment to USC for installing of "stand-alone" debs.   Normally, for most Epson and HP printers, you should only be installing via "debs" versus other methods such as shell scripts or source code.
3.  The openprinting org website is where you want to go to find your drivers.
4.  In this case - start by installing the deb "1.0.2 (DEB for LSB 3.2)" . . . found here:   [http://www.openprinting.org/printer/Epson/Epson-WP-4020](http://www.openprinting.org/printer/Epson/Epson-WP-4020)
5.  Right click on the file after download, and select either the USC . . . . . . OR . . . .  gdebi to do the install (for stand-alone debs like this, I actually prefer gdebi to USC)
6.  IF needed - check in your Systems Settings to see if printer is added as your default printer (I tend to do this step first, as it can simplify everything automagically)
7. (Optional Step) You can also add "http:download.ebz.epson.net/dsc/op/stable/debian/lsb3.2 main"  to (System Settings>Software & Updates>Other Software) and then the USC will have these drivers available to search & select for install (via the "All Software" drop-down arrow).

---

### Post by Mike_Walsh on 2014-12-13
> **JeQhdMD said:**
> Holy Pete!  . . 100% agree with Mike that you're doing this the "hard way" . . . 

1.   When you get your system un-hosed, open Ubuntu Software Center (USC) & install "Synaptic" (if not already installed),
2.  Find and install "gdebi" package manager . . . this is a useful compliment to USC for installing of "stand-alone" debs.   Normally, for most Epson and HP printers, you should only be installing via "debs" versus other methods such as shell scripts or source code.
3.  The openprinting org website is where you want to go to find your drivers.
4.  In this case - start by installing the deb "1.0.2 (DEB for LSB 3.2)" . . . found here:   [http://www.openprinting.org/printer/Epson/Epson-WP-4020](http://www.openprinting.org/printer/Epson/Epson-WP-4020)
5.  Right click on the file after download, and select either the USC . . . . . . OR . . . .  gdebi to do the install (for stand-alone debs like this, I actually prefer gdebi to USC)
6.  IF needed - check in your Systems Settings to see if printer is added as your default printer (I tend to do this step first, as it can simplify everything automagically)
7. (Optional Step) You can also add "http:download.ebz.epson.net/dsc/op/stable/debian/lsb3.2 main"  to (System Settings>Software & Updates>Other Software) and then the USC will have these drivers available to search & select for install (via the "All Software" drop-down arrow).

+1 to THAT.

Aye, I'd forgotten about gdebi. It DOES do a far better job for standalone debs, as far as installing goes. Synaptic is better for complete removal, though.

Yes, I must agree with you. It won't hurt in the slightest to have both Epson's 'generic' driver, AND the more specific driver for THAT particular printer. You then have both available, and this is a good thing.....I'll explain why.

I find that for the local printer, you're better with the specific driver for the printer. Should you wish to do network printing from another machine, in my experience you're better to install the generic driver in the client machine. If you install the specific driver for both client AND host machines, CUPS doesn't seem to like it.....UNLESS you rename your network printer differently to the host printer. This is just the way it seems to work.....at least for EPSON machines.

Regards,

Mike.

---

### Post by Randyman99 on 2015-04-13
Sorry to take so long to get back. I've been around the world with different Linux distros, and have moved up to Ubuntu 64 bit as one of them. I also have Ubu 64 bit running on a second machine, and needed to install the same print driver on that, which brought me to revisit this page, as installing this printer is an extra effort with every distro I have. 

**JeQhdMD**, you were completely right. I followed your instructions through number 5, using gdebi to install the package. It worked flawlessly, and made installation a breeze. After that, I went into CUPS and installed the printer, and it selected the correct driver by default. I was then able to set the default configuration and set the printer as the default from within CUPS. Thanks to you and Mike both for helping me out. I'll mark this as solved.

---

