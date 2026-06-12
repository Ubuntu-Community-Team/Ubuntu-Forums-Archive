---
title: "How to Install a file with extension .run"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by Bumpalot on 2011-10-26
I want to install ati-driver-installer-11-9-x86.x86_64.run
Any suggestions?

---

### Post by haqking on 2011-10-26
> **Bumpalot said:**
> I want to install ati-driver-installer-11-9-x86.x86_64.run
Any suggestions?

```
 ./ati-driver-installer-11-9-x86.x86_64.run
```

or

```
sh ati-driver-installer-11-9-x86.x86_64.run
```

make sure you are in the right location though, ie the location of the .run file

---

### Post by 3rdalbum on 2011-10-26
> **Bumpalot said:**
> I want to install ati-driver-installer-11-9-x86.x86_64.run
Any suggestions?

Instead of doing that, go to the Additional Drivers program on your computer. It will download and install a more convenient driver for you.

The only time you should manually install a graphics driver like that is when you're using an old OS with a new graphics card.

---

### Post by Bumpalot on 2011-10-26
In Ubuntu 10.02 "Hardware Drivers" (no "Additional Drivers") reports "No proprietary drivers are in use on this system". 
What I want to do is install ATI Catalyst Installer (Ubuntu Community Help suggested ati-driver-installer-11-9-x86.x86_64.run) so I have downloaded (not sure if it is compatible though!). Currently I have AMD Radeon 4200HD installed (motherboard). I haven't a clue as to how I can install it. Would appreciate any constructive suggestions.

---

### Post by Vaphell on 2011-10-26
i've heard that catalyst 11.9 is not so good
either way run synaptic and look for fglrx first

if you more up-to-date version of drivers try x-swat PPA
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

you can enable it in ubuntu-tweak tool (sudo apt-get install ubuntu-tweak), it's called 'x updates'

---

### Post by 3rdalbum on 2011-10-26
> **Vaphell said:**
> i've heard that catalyst 11.9 is not so good
either way run synaptic and look for fglrx first

He's using 10.04; I think the fglrx in 10.04 predates his graphics card.

---

### Post by Vaphell on 2011-10-26
computer i am using now has a mobo with 4200 integrated video, for over 1 year i ran lucid on it (i still do, but now i have discrete 6850). I am 99% sure that fglrx was in use all that time. If the driver is too old, x-swat ppa will solve it.

Either way running that amd installer is not so healthy for the system because it operates out of scope of package manager and can mess things up. Imo you shouldn't do manual install behind apt-get's back if you lack skill or will to clean up the mess when something bad happens.

---

### Post by Bumpalot on 2011-10-26
Followed your advice.
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
What happened here ???
According to the info on the PPA Description:
"If you are uprading from one release to another with this PPA activated,  please install the ppa-purge package and use it to downgrade everything  in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it."
I tried that;
bumpy@bumpyputer:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo: ppa-purge: command not found
Now I'm completely lost!!!

---

### Post by Vaphell on 2011-10-26
you registered new software repository, now let the package manager know the current status (update) and actualize installed packages (upgrade)
```
sudo apt-get update && sudo apt-get upgrade
```
or click refresh in software center or in synaptic or in update manager
now look for fglrx and fglrx-amdcccle or
```
sudo apt-get install fglrx flgrx-amdcccle
```

---

### Post by audiomick on 2011-10-26
> **Bumpalot said:**
> Followed your advice.
...What happened here ???
According to the info on the PPA Description:
"If you are uprading from one release to another with this PPA activated, [COLOR=Red]** please install the ppa-purge package**[/COLOR] and use it to downgrade everything  in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it."
I tried that;
bumpy@bumpyputer:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo: ppa-purge: command not found
Now I'm completely lost!!!
The output of your first commands looks ok to me. It looks like a PPA was added, but that the required key for it was already there.

Your second command did not work because the package ppa-purge is not installed, I guess. You can get this package from synaptic, if you have it, or the software center. While you are there, you can look at your package sources (edit menu in software center, preferences menu in synaptic) to see if the ppa that you installed in the first bit of your post is really there.

---

### Post by Bumpalot on 2011-10-26
bumpy@bumpyputer:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) lucid/main Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Reading package lists... Done

Is this good news?? - what next?

---

### Post by Vaphell on 2011-10-26
yes it is, no problem here
```
sudo apt-get upgrade
sudo apt get install fglrx fglrx-amdcccle
```

upgrade will upgrade currently installed packages, next line will install the driver and catalyst control center

EDIT:
wait what? ignored? can you go to Software sources to the 3rd party sources tab and see if the checkbox for x-swat is ticked? because it looks like the repo is added but disabled

---

### Post by Bumpalot on 2011-10-26
check box is ticked.
bumpy@bumpyputer:~$ sudo apt-get install fglrx flgrx-amdcccle
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bumpy@bumpyputer:~$ sudo apt get install fglrx fglrx-amdcccle
sudo: apt: command not found

---

### Post by Vaphell on 2011-10-26
only one program at a time can work with packages - close synaptic or whatever

it's apt-get not apt get
highlight commands here and paste them with middle click in terminal, you don't have to type everything

---

### Post by Bumpalot on 2011-10-26
bumpy@bumpyputer:~$ sudo apt-get install fglrx flgrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
E: Couldn't find package flgrx-amdcccle

---

### Post by Vaphell on 2011-10-26
1. oops, typo f**gl**rx-amdcccle not f**lg**rx
2. crap, you have it installed already but not in use :/
so you are saying that jockey-gtk (Hardware Drivers) doesn't detect fglrx as available to use?

---

### Post by Bumpalot on 2011-10-26
bumpy@bumpyputer:~$ sudo apt-get install flgrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flgrx-amdcccle

---

### Post by audiomick on 2011-10-26
> **Bumpalot said:**
> bumpy@bumpyputer:~$ sudo apt-get install fglrx flgrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
E: Couldn't find package[COLOR=Red]** flgrx-**[/COLOR]amdcccle

looks like you typed it wrong. fglrx, isn't it?

---

### Post by Bumpalot on 2011-10-26
oops - sorry about that -am just learning!!
bumpy@bumpyputer:~$ sudo apt-get install amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amdcccle

---

### Post by Vaphell on 2011-10-26
lol, you haven't fixed the typo, it still says flg... not fgl...
edit: and now you left the fglrx part, it's **fglrx-amdcccle**

if you are not sure about exact names
```
apt-cache search fglrx
``` will do a search and print out all related packages so you don't have to depend on random people on internet ;-)
if you don't like command line you can do the same in clicky-clicky synaptic :)

so Hardware Drivers doesn't see the drivers as available?

---

### Post by Bumpalot on 2011-10-26
bumpy@bumpyputer:~$ apt-cache search fglrx
jockey-common - user interface and desktop integration for driver management
jockey-gtk - GNOME user interface and desktop integration for driver management
jockey-kde - KDE user interface and desktop integration for driver management
xorg-driver-fglrx - Transitional package for xorg-driver-fglrx
fglrx-kernel-source - Transitional package for fglrx-kernel-source
xserver-xorg-video-radeon - X.Org X server -- AMD/ATI Radeon display driver
fglrx-modaliases - Identifiers supported by the ATI graphics driver
fglrx-dev - Video driver for the ATI graphics accelerators (devel files)
fglrx-amdcccle - Catalyst Control Center for the ATI graphics accelerators
fglrx - Video driver for the ATI graphics accelerators

---

### Post by Vaphell on 2011-10-26
as you see these are packages related to fglrx, you have the proper name of catalyst before your eyes, now sudo apt-get install it :) you can highlight-middleclick-paste it to avoid typos.

---

### Post by Bumpalot on 2011-10-26
bumpy@bumpyputer:~/Downloads$ cd ATICatalystInstaller
bumpy@bumpyputer:~/Downloads/ATICatalystInstaller$ sudo apt-get ati-driver-installer ati-driver-installer-11-2-x86.x86_64.run
E: Invalid operation ati-driver-installer

---

### Post by Vaphell on 2011-10-26
before you go manual istallation way, answer me this:
does the Hardware drivers detect anything?

and apt-get is only for repositories
when you want to run 'normal' files you need to:
```
chmod +x <filename>
./<filename>
```

chmod +x adds executable bit
considering this file wants to install to system directories sudo will be required (sudo ./<filename)

---

### Post by ubupirate on 2011-10-26
> **Bumpalot said:**
> I want to install ati-driver-installer-11-9-x86.x86_64.run
Any suggestions?

Right click, goto Permissions tab, check Execute as Program.

Double click the file, select run from terminal. Follow instructions, reboot after installed.

---

### Post by Bumpalot on 2011-10-26
bumpy@bumpyputer:~/Downloads/ATICatalystInstaller$ sudo chmod +x ati-driver-installer-11-2-x86.x86_64.run
bumpy@bumpyputer:~/Downloads/ATICatalystInstaller$ sudo ./ati-driver-installer-11-2-x86.x86_64.run
Created directory fglrx-install.Mx9T4O
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.32-34-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.Mx9T4O

---

### Post by Bumpalot on 2011-10-26
Accoring to the ATI pdf, 
System Recommendations
For optimal performance and ease of use, the following are available:
Kernel module build environment
o Kernel source code include either the Kernel Source or Kernel Headers packages
The RPM utility should be installed and configured correctly on your system, if you
intend to install via RPM packages
The following packages must be installed in order for the AMD Catalyst driver for Linux
to install and work optimally:
XFree86-Mesa-libGL
libstdc++
libgcc
XFree86-libs
fontconfig
freetype
zlib
gcc
How do I find out if any of the above are installed or not?

---

### Post by Bumpalot on 2011-10-26
Am currently using Synaptic to determine which packages need to be installed.
Will post this SAP

---

### Post by Bumpalot on 2011-10-26
Not installed
-------------
XFree86-Mesa-libGL
XFree86
xFree86-libs
freetype
libcc

Installed
---------
freetype2-demos
fontconfig
gcc
libcc1
libcc1-dbg
libstdc++6
zlib

How do I install the missing items?

---

### Post by Bumpalot on 2011-10-26
Also
Installled
glibc-doc

Not Installed
glibc
POSIX Shared Memory /dev/shm (for 3D application - I don't need this)

---

