---
title: "Installing package"
date: 2019-04-02
forum: Packaging and Compiling Programs
---

### Post by anneranch on 2019-04-02
Installing package 
I am in a process of installing libbluetooth-dev package for armhf architecture. 
I have downloaded libbluetooth-dev_5.50-1_armhf.deb
and was unsuccessful in using 

R CMD INSTALL libbluetooth-dev_5.50-1_armhf.deb

I did try both  libbluetooth-dev_5.50-1_armhf.deb and "extracted"  libbluetooth-dev_5.50-1_armhf
from the folder where they currently are.


> 
jim@jim-desktop:/media/jim/DEV/BLUETOOTH$ ls
bt_c      libbluetooth-dev_5.50-1_amd64      libbluetooth-dev_5.50-1_armhf
bt_c.zip  libbluetooth-dev_5.50-1_amd64.deb  libbluetooth-dev_5.50-1_armhf.deb
jim@jim-desktop:/media/jim/DEV/BLUETOOTH$ R CMD libbluetooth-dev_5.50-1_armhf.deb
/usr/lib/R/bin/Rcmd: 62: exec: libbluetooth-dev_5.50-1_armhf.deb: not found
jim@jim-desktop:/media/jim/DEV/BLUETOOTH$ R CMD libbluetooth-dev_5.50-1_armhf
/usr/lib/R/bin/Rcmd: 62: exec: libbluetooth-dev_5.50-1_armhf: not found




Per R documentation the CMD INSTALL expect "tar" file format. 

I am stuck. 

What other options I have to install libbluetooth-dev_5.50-1_armhf.deb?

I did extract the libbluetooth-dev_5.50-1_armhf.deb and ended up with two "tar" files. 

I did look for "INSTALL" script but no luck.


Actually - how did "extract" work if the libbluetooth-dev_5.50-1_armhf.deb is not recognized by R as "tar"?

It would help if I can read-up on how Linux packages are handled in the first place. 
Mr Google did not help. 


Thanks, any help will be appreciated.




After I  posted the above I tried this 




> 

jim@jim-desktop:/media/jim/DEV/BLUETOOTH$ sudo apt install ./libbluetooth-dev_5.50-1_armhf.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libbluetooth-dev:armhf' instead of './libbluetooth-dev_5.50-1_armhf.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libbluetooth-dev:armhf : Depends: libbluetooth3:armhf (= 5.50-1) but it is not installable
                          Depends: libc6-dev:armhf but it is not installable or
                                   libc-dev:armhf but it is not installable
E: Unable to correct problems, you have held broken packages.
jim@jim-desktop:/media/jim/DEV/BLUETOOTH$ 








Now the "problem" is now to satisfy the dependencies.
Perhaps "dpkg" is next to try. 

PS  I did  run update /upgrade , no difference.

---

### Post by TheFu on 2019-04-02
First, manually downloading a package to be installed is an anti-pattern.  Linux package management handles that for you, gets the package from the correct repository, validates it with cryptographic signatures and installs it, along with any required dependencies.

```
sudo apt install  libbluetooth-dev
```
should do it. I tested it on my 16.04 x64 laptop and that did what was expected.

In very special situations, you might need to get more manual, but that almost always means you are either a software developer or doing something the hard way. I'm making all sorts of assumptions based on the question and what you've written. Seems you are very new to Linux and package management.

If my answer isn't what you need, for specific reasons, there are harder ways.

[https://blog.jdpfu.com/2015/02/08/linux-package-install-preferences](https://blog.jdpfu.com/2015/02/08/linux-package-install-preferences) explains the order that packages should be seek to be installed. Grabbing a .deb file is #4 in my list. 3 better options.

---

### Post by monkeybrain20122 on 2019-04-02
??? Why would you try to use R to install a .deb??!!  I am afraid it makes no sense at all. R CMD installs R packages, not any software.

---

### Post by TheFu on 2019-04-02
I'm thinking a quick read over this: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) by the OP would be helpful.

Package Management for different distros explained: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html#mozTocId691245](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html#mozTocId691245)
and the normal wikipedia article: [https://en.wikipedia.org/wiki/Package_management_system](https://en.wikipedia.org/wiki/Package_management_system)

But if the OP is trying to do something very specialized, we'd need more information.  Like installing a very specific version of 1 thing cascades across many other packages and is probably best handled inside a chroot or container or VM to avoid messing with a normal desktop.  This assumes a PPA isn't available with all the dependencies already handled.

---

### Post by anneranch on 2019-04-02
Since I am asking same in different forums here is a copy of my log,

I did try to verify . add access to deb repository - as I seen in another, unresolved post,  with same issue. 
The log shows
 E: Unable to locate package libbluetooth-dev:armhf 

and when I  reinstall libbluetooth-dev I "get it" from 

[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libbluetooth-dev amd64 5.37-0ubuntu5.1

Now the simple question - apparently  the installed "deb " repository is nowhere or inaccessible ? 
How do I
verify that and actually added  it ?

At this point I am not concerned having two package of same name, I 'll can tackle that later - now I really need some assistance in actualy installing the deb package for armhf. First thing first. 

LOG copy 

```
jim@jim-desktop:~$ sudo apt-get install libbluetooth-dev:armhf 
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Unable to locate package libbluetooth-dev:armhf
```

```

jim@jim-desktop:~$ sudo apt-get install libbluetooth-dev 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following NEW packages will be installed:
  libbluetooth-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 145 kB of archives.
After this operation, 570 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libbluetooth-dev amd64 5.37-0ubuntu5.1 [145 kB]
Fetched 145 kB in 0s (217 kB/s)          
Selecting previously unselected package libbluetooth-dev.
(Reading database ... 297300 files and directories currently installed.)
Preparing to unpack .../libbluetooth-dev_5.37-0ubuntu5.1_amd64.deb ...
Unpacking libbluetooth-dev (5.37-0ubuntu5.1) ...
Setting up libbluetooth-dev (5.37-0ubuntu5.1) ...
jim@jim-desktop:~$
```

Update 
foudn part of the problem - my TYPO !
```
jim@jim-desktop:~$ grep ^[^#] /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list:deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial contrib
/etc/apt/sources.list:deb [arch=amd64,i386] [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) xenial main universe
```


/etc/apt/sources.list:deb [[COLOR=#ff0000]arch=i386,amrhf[/COLOR]] [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) xenial main universe

this should be [arch=amd64, armhf ]

```
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-xenial.list:deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial main
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-xenial.list.save:deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial main
/etc/apt/sources.list.d/hanipouspilot-ubuntu-bluetooth-xenial.list:deb [http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu](http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu) xenial main
/etc/apt/sources.list.d/hanipouspilot-ubuntu-bluetooth-xenial.list.save:deb [http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu](http://ppa.launchpad.net/hanipouspilot/bluetooth/ubuntu) xenial main
/etc/apt/sources.list.d/js-reynaud-ubuntu-kicad-5-xenial.list:deb [http://ppa.launchpad.net/js-reynaud/kicad-5/ubuntu](http://ppa.launchpad.net/js-reynaud/kicad-5/ubuntu) xenial main
/etc/apt/sources.list.d/js-reynaud-ubuntu-kicad-5-xenial.list.save:deb [http://ppa.launchpad.net/js-reynaud/kicad-5/ubuntu](http://ppa.launchpad.net/js-reynaud/kicad-5/ubuntu) xenial main
/etc/apt/sources.list.d/nodesource.list:deb [https://deb.nodesource.com/node_10.x](https://deb.nodesource.com/node_10.x) xenial main
/etc/apt/sources.list.d/nodesource.list:deb-src [https://deb.nodesource.com/node_10.x](https://deb.nodesource.com/node_10.x) xenial main
/etc/apt/sources.list.d/nodesource.list.save:deb [https://deb.nodesource.com/node_10.x](https://deb.nodesource.com/node_10.x) xenial main
/etc/apt/sources.list.d/nodesource.list.save:deb-src [https://deb.nodesource.com/node_10.x](https://deb.nodesource.com/node_10.x) xenial main
/etc/apt/sources.list.d/openscad-ubuntu-releases-xenial.list:deb [http://ppa.launchpad.net/openscad/releases/ubuntu](http://ppa.launchpad.net/openscad/releases/ubuntu) xenial main
/etc/apt/sources.list.d/openscad-ubuntu-releases-xenial.list.save:deb [http://ppa.launchpad.net/openscad/releases/ubuntu](http://ppa.launchpad.net/openscad/releases/ubuntu) xenial main
/etc/apt/sources.list.d/shutter-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) xenial main
/etc/apt/sources.list.d/shutter-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) xenial main
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial main
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list.save:deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial main
```

---

### Post by anneranch on 2019-04-03
Let me start over. 
I have decided to try this resource 

[https://launchpad.net/ubuntu/disco/+package/libbluetooth3-dbg](https://launchpad.net/ubuntu/disco/+package/libbluetooth3-dbg)


after I select the version I want I get this 

[https://launchpad.net/ubuntu/disco/armhf/libbluetooth3-dbg/5.50-0ubuntu2](https://launchpad.net/ubuntu/disco/armhf/libbluetooth3-dbg/5.50-0ubuntu2)

then I select "downloadable file" 
[libbluetooth3-dbg_5.50-0ubuntu2_armhf.deb]("http://launchpadlibrarian.net/406232591/libbluetooth3-dbg_5.50-0ubuntu2_armhf.deb")

Ubuntu slower then molasses "Software Instillation" takes over and install this:

```
jim@jim-desktop:~$ dpkg -l "libblue*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-
ii  libbluetooth-dev            5.37-0ubuntu5.1    amd64              Development files for using the BlueZ Linux Bluetooth libra
ii  libbluetooth3:amd64         5.37-0ubuntu5.1    amd64              Library to use the BlueZ Linux Bluetooth stack
ii  libbluetooth3:i386          5.37-0ubuntu5.1    i386               Library to use the BlueZ Linux Bluetooth stack
**ii  libbluetooth3-dbg           5.37-0ubuntu5.1    amd64              Library to use the BlueZ Linux Bluetooth stack with debuggi**
un  libbluetooth3-dev           <none>             <none>             (no description available)
```


**I did expect "armhf" architecture and  version 5.50 **

Where did I go wrong?

---

### Post by Frogs Hair on 2019-04-03
Using a package from an unreleased version of Ubuntu may be part of the problem. There can be dependency differences in each release.

---

### Post by anneranch on 2019-04-03
Thanks for reply.
Hopefully not, because I have had  same issues with releases. 

So far when I was able to install the initial package ( of wrong architecture ) then the issues with dependencies  showed up.

At this point the version is not a big issue, the architecture is. 

When I can get correct architecture , then I should be able to tackle the dependencies.

---

### Post by TheFu on 2019-04-03
Architectures matter for any compiled software ... like drivers and libraries.  They are not interchangeable.

Scripts and config files are usually architecture independent and compiled Java, but not C, C++ or any of the other binary compiled languages.
Having packages with the wrong architecture installed is never good and can only cause problems.

---

