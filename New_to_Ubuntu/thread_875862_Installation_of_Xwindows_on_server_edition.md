---
title: "Installation of Xwindows on server edition"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by cranston on 2008-07-31
i am trying to install xwindows onto the latest server edition of ubuntu.  i have a directory called X11 but nowhere on the system do i have the xorg.conf file.  when i try to install the package xserver-xorg-core_1.4.2-2_i386.deb i get the error message "couldn't find any package whose name or description that matched xserver-xorg-core_1.4.2-2_i386.deb. Any ideas will be greatly appreciated 

PS i am installing this package for my own educational purposes

PPS I would like to thank the people who came up with a solution to my problem of installing rpm onto ubuntu. i did not get back to them as i could not find the thread. so once again thanks for the help

---

### Post by aeiah on 2008-07-31
do 
```
sudo apt-get install xorg
```

but instead of pressing enter, press tab and see what choices you have. im not on my linux machine right now so i cant check, but i imagine the package you want will be available. you could also install a full desktop which would install it if you wanted

---

### Post by halitech on 2008-07-31
have you downloaded the file or are you doing sudo apt-get install xserver-xorg?

ps. if you click on the link that says USER CP, that will take you to a list of all threads you have posted in

---

### Post by cranston on 2008-07-31
i have download the package from a mirror somewhere. transferred from my windows PC via a cdrom and have tried to install the package after mountin the Cd drive.   i have tried what you have sugested but without any success.  

PS boy are you guys quick with the responses

---

### Post by cranston on 2008-07-31
i have also tried the command suggested sudo apt-get install xorg.  the message i get is 'couldn't find package xorg

i have also tried the command sudo apt-get install /media/cdrom0/xserver-xorg-core_1.4.2-2_i386.deb with the message described initially

---

### Post by aeiah on 2008-07-31
yea the apt-get install xorg thing was my mistake. i couldnt check because im on a windows box right now. it'd probably be sudo aptget install xserver (then press tab to get a list of files if there are a few)

how come your server isnt connected to the internet? thats a little bit strange isnt it? ;)

do you have a desktop edition cd that matches your server? (ie you have ubuntu server 8.04 and ubuntu desktop 8.04), because you can use the repository on the ubuntu desktop cd, which will surely contain all the xserver bits and pieces you'll need and all be of the correct version.


or are you just having a problem installing a perfectly good .deb file perhaps?

on the CLI navigate to where your .deb file is
```

cd /media/cdrom0/
```

then do

```

sudo dpkg -i xserver-xorg-core_1.4.2-2_i386.deb
``` (just type the xserver part of the name and use tab to auto-complete the last part)

that is the way you install .deb from the command line, which is probably what you've been asking from the beginning but i wasnt paying enough attention, sorry.

---

### Post by halitech on 2008-07-31
I was just going to go looking for that command :D thanks

---

### Post by sisco311 on 2008-07-31
you can add the desktop cd to the source list and
use apt-get to install the package with all the dependencies:

insert the disk:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install xorg
```aptitude show xorg
> Package: xorg
State: installed
Automatically installed: yes
Version: 1:7.3+10ubuntu10.2
Priority: optional
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 24.6k
Depends: libgl1-mesa-glx | libgl1, libglu1-mesa, x11-apps, x11-common,
         x11-session-utils, x11-utils, x11-xfs-utils, x11-xkb-utils,
         x11-xserver-utils, xauth, xfonts-100dpi (>= 1:1.0.0-1), xfonts-75dpi
         (>= 1:1.0.0-1), xfonts-base (>= 1:1.0.0-1), xfonts-scalable (>=
         1:1.0.0-1), xfonts-utils, xinit, xkb-data, xserver-xorg, xterm |
         x-terminal-emulator
Suggests: xorg-docs
Provides: x-window-system, x-window-system-core
Description: X.Org X Window System
 This metapackage provides the components for a standalone workstation running
 the X Window System.  It provides the X libraries, an X server, a set of fonts,
 and a group of basic X clients and utilities. 
 
 Higher level metapackages, such as those for desktop environments, can depend
 on this package and simplify their dependencies. 
 
 It should be noted that a package providing x-window-manager should also be
 installed to ensure a comfortable X experience.
aptitude show xserver-xorg
> Package: xserver-xorg
State: installed
Automatically installed: no
Version: 1:7.3+10ubuntu10.2
Priority: optional
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 623k
Depends: debconf (>= 0.5) | debconf-2.0, mdetect, x11-xkb-utils, xkb-data |
         xkb-data-legacy, xserver-xorg-core (>= 2:1.4-3), xserver-xorg-input-all
         | xserver-xorg-input-2, xserver-xorg-video-all | xserver-xorg-video-2
PreDepends: x11-common (>= 1:7.3+3)
Recommends: displayconfig-gtk, dmidecode, laptop-detect, libgl1-mesa-dri, udev
Conflicts: xserver-common, xserver-xfree86 (< 6.8.2.dfsg.1-1)
Replaces: xserver-common
Description: the X.Org X server
 This package depends on the full suite of the server and drivers for the X.Org
 X server, as well as providing a configuration infrastructure to manage
 xorg.conf.  **It does not provide the actual server itself**, but removing it is
 strongly discouraged.

---

### Post by cranston on 2008-07-31
thanks aeiah.  this the command has got further then i previously had. now though it shows a whole heap of dependecies that are missing. i will now plough on and install the missing dependencies.  

once againn thanks to you all

---

### Post by aeiah on 2008-07-31
you'll find it much easier to either use an online repository or use one located on a cd (ie, the ubuntu desktop cd) than to track down all the dependencies. the dependencies you get will probably have dependencies of their own you see.

sisco311's post on how to use the cd's repository should help you. but i guess if your internet is slow and you dont have the desktop cd, you may have to go with downloading all the .debs :(

---

### Post by JoneYee on 2008-07-31
When I installed server, to get xwindows/gui i typed:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by halitech on 2008-07-31
that will install all the packages associated with Ubuntu, by the sounds of it, they are just looking for the gui and nothing more (at least right now)

---

