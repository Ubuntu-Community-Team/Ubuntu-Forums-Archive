---
title: "no video no audio ,greenish video with buffering"
date: 2015-03-16
forum: New to Ubuntu
---

### Post by amrithmmh on 2015-03-16
i installed ubuntu 14.04.2 my specs 6 gb ram, 2gb graphics amd  dual, amd processor a6 @2.4 ghz   problems: 1.video problem...graphics flglx cannot be installed.....bug already present 2 no sound 3.EXTREME HEATING ...I CAN COOK FOOD USING MY LAPTOP 4.lag even while presssing dash button  please help should i get back to windows?  i dont want to..

---

### Post by amrithmmh on 2015-03-17
please reply i really want to shift from windows

---

### Post by dino99 on 2015-03-17
to narrow down your issues, you can :
- purge then reinstall the graphic driver
- use system-monitor / htop to find which processes are using too much cpu %
- glance at your logs to find something usefull (warnings/errors)
- boot with an older kernel
- downgrade packages, in case of ppa used
- ....

---

### Post by Geoffrey_Arndt on 2015-03-17
The main issue is with the lack of driver install.   How did you try to install the driver, and what error/bug info do you have (details helpful).

In short, you must figure out how to install the proprietary drivers and if that's not done, then you need to run a lighter version of ubuntu (than the standard with Unity).

Ubuntu Mate seems to be getting great reviews, is very fast and does not require proprietary drivers for general (non-gaming) use.

---

### Post by newb85 on 2015-03-17
Specifics on your graphics card would also be helpful.  The output of 
```

sudo lshw -C display
```
should do the trick.

*If you're not running from the live media, it will ask for a password.  It's the password for your user login.  It won't give any visual feedback as you type the password.  That's normal*

---

### Post by amrithmmh on 2015-03-18
*-display UNCLAIMED     
       description: VGA compatible controller
       product: Trinity [Radeon HD 7520G]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff ioport:3000(size=256) memory:f0300000-f033ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Thames [Radeon HD 7500M/7600M Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f0200000-f021ffff ioport:2000(size=256) memory:f0220000-f023ffff
amrock@amrock-LENOVO-IdeaPad-Z585:~$

---

### Post by amrithmmh on 2015-03-18
BUG


   [h=1][[Desktop-packages] [Bug 1424491] Re: apt-get fails to install fglrx or fglrx-updates in 14.04.2 and 12.04.5]("https://www.mail-archive.com/search?l=desktop-packages@lists.launchpad.net&q=subject:%22%5BDesktop-packages%5D+%5BBug+1424491%5D+Re%3A+apt-get+fails+to+install+fglrx+or+fglrx-updates+in+14.04.2+and+12.04.5%22&o=newest")[/h] 


 ** Changed in: fglrx-installer (Ubuntu)        Status:
Triaged => In Progress ** Changed in: fglrx-installer-updates (Ubuntu)        Status: Confirmed => In Progress 

** Changed in: fglrx-installer-updates (Ubuntu)    Importance: Undecided => High 

** Changed in: fglrx-installer-updates (Ubuntu)      Assignee: (unassigned) => Alberto Milone
(albertomilone) 

** Changed in: fglrx        Status: New => Invalid 

-- 
You received this bug notification because you
are a member of Desktop Packages, which is subscribed to fglrx-installer
in Ubuntu. [https://bugs.launchpad.net/bugs/1424491](https://bugs.launchpad.net/bugs/1424491) 

Title:   apt-get fails to install fglrx or
fglrx-updates in 14.04.2 and 12.04.5 

Status in AMD fglrx video driver:   Invalid Status in fglrx-installer package in Ubuntu:   In Progress Status in fglrx-installer-updates package in
Ubuntu:   In Progress 

Bug description:   Activity:  Install fglrx AMD driver on 12.04.5
and 14.02.2 

  Expected behavior:  fglrx would intall 

  Observed behavior:  fglrx is not installed as
follows 

  Attempt to install fglrx fails as follows: 

          zack3@ZACK3:~$
sudo apt-get install fglrx-updates xvba-va-driver           Reading
package lists... Done           Building
dependency tree           Reading
state information... Done           Some
packages could not be installed. This may mean that you have           requested
an impossible situation or if you are using the unstable           distribution
that some required packages have not yet been created           or
been moved out of Incoming.           The
following information may help to resolve the situation: 

          The
following packages have unmet dependencies:            fglrx-updates
: Depends: xorg-video-abi-11 but it is not installable 
or  
                                  xorg-video-abi-12
but it is not installable 
or  
                                  xorg-video-abi-13
but it is not installable 
or  
                                  xorg-video-abi-14
but it is not installable 
or  
                                  xorg-video-abi-15           E:
Unable to correct problems, you have held broken packages. 

  Attempt to insatll xorg-video-abi-15 yields: 

          zack3@ZACK3:~$
sudo apt-get install xorg-video-abi-15           Reading
package lists... Done           Building
dependency tree           Reading
state information... Done           Note,
selecting 'xserver-xorg-core' instead of 'xorg-video-abi-15'           Some
packages could not be installed. This may mean that you have           requested
an impossible situation or if you are using the unstable           distribution
that some required packages have not yet been created           or
been moved out of Incoming.           The
following information may help to resolve the situation: 

          The
following packages have unmet dependencies:            libcheese-gtk23
: Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it 
is not going to be installed                              Depends:
libcogl15 (>= 1.15.8) but it is not going 
to be installed            libcheese7
: Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not 
going to be installed                         Depends:
gstreamer1.0-clutter but it is not going to be 
installed            libclutter-1.0-0
: Depends: libcogl-pango15 (>= 1.15.8) but it is 
not going to be installed                               Depends:
libcogl15 (>= 1.15.8) but it is not 
going to be installed           E:
Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

  Attempting to install xserver-xorg-core
instead yields: 

          zack3@ZACK3:~$
sudo apt-get install xserver-xorg-core           Reading
package lists... Done           Building
dependency tree           Reading
state information... Done           Some
packages could not be installed. This may mean that you have           requested
an impossible situation or if you are using the unstable           distribution
that some required packages have not yet been created           or
been moved out of Incoming.           The
following information may help to resolve the situation: 

          The
following packages have unmet dependencies:            libcheese-gtk23
: Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it 
is not going to be installed                              Depends:
libcogl15 (>= 1.15.8) but it is not going 
to be installed            libcheese7
: Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not 
going to be installed                         Depends:
gstreamer1.0-clutter but it is not going to be 
installed            libclutter-1.0-0
: Depends: libcogl-pango15 (>= 1.15.8) but it is 
not going to be installed                               Depends:
libcogl15 (>= 1.15.8) but it is not 
going to be installed           E:
Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

To manage notifications about this bug go to: [https://bugs.launchpad.net/fglrx/+bug/1424491/+subscriptions](https://bugs.launchpad.net/fglrx/+bug/1424491/+subscriptions)

---

### Post by amrithmmh on 2015-03-18
i dont know what to do ? will the bug be fixed i dont have access to very high speed internet to download another version ...it took me great pain to beat windows uefi to install ubuntu but now am heartbroken:mad:

---

### Post by Geoffrey_Arndt on 2015-03-18
Maybe one alternative would be to use a torrent file to get the latest Xubuntu or Ubuntu Mate.  For example, you could let it run overnight (or even into the next day if needed.)   The install media (dvd or usb fllash-stick) is also available via mail (check out [https://www.osdisc.com/index.html?affiliate=distrowatch](https://www.osdisc.com/index.html?affiliate=distrowatch)).

The install (hopefully) would be simpler than the original as you can replace or overlay the existing install.

And yet another option is just to install the latest XFCE desktop from the Ubuntu Software Center, and upon the next boot-up, there should be an clickable option on the user log-in window to select an alternative "DE" (desktop) . . . in this case XFCE.   Then, there would be some work to get it looking good (that's why getting the actual install media is simpler because the Desktop Environment setup is pre-configured for you.)

Perhaps another Ubuntu forum member is familiar with the bug, and if there is a work-around that can be done.

---

### Post by newb85 on 2015-03-19
If you go the route of installing the XFCE DE, know this:

If you install the package xubuntu-desktop, it will install the DE, the artwork (backgrounds, colors, fonts, etc), and the default apps.  The drawback here is that you'll have multiple apps that do the same thing.
If you install just xfce4, it will be just the DE, without the artwork.  That's why Geoffrey says there would be some work to get it looking good.
If you install xubuntu-default-settings along with xfce4, it will bring in the artwork.  The drawback here is it will also impact the unity DE (in terms of colors, fonts, etc.).

---

