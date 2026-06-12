---
title: "Issues with Lenovo Touchpad"
date: 2015-10-23
forum: New to Ubuntu
---

### Post by Travis_Olsen on 2015-10-23
Hello all, 

I just installed Ubuntu 14.04 on a new laptop and  can't get the touchpad to work. I've browsed other threads on the topic,  but can't find one with the exact same issue. I know there are bugs  with certain touchpads, though it seems this one is recognized but not  working due to some issue with broken/held synaptics packages. Here's  what I've attempted so far:

travis@travis-Lenovo-S21e-20:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SYNA2B27:00 06CB:2956                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; SteelSeries Rival Gaming Mouse              id=12    [slave  pointer  (2)]
&#9116;   &#8627; SteelSeries Rival Gaming Mouse              id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; SteelSeries Rival Gaming Mouse              id=14    [slave  keyboard (3)]

travis@travis-Lenovo-S21e-20:~$ sudo apt-get install xserver-xorg-input-synaptics
[sudo] password for travis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-input-synaptics : Depends: xorg-input-abi-20
                                Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.

travis@travis-Lenovo-S21e-20:~$ sudo apt-get install xorg-input-abi-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xserver-xorg-core' instead of 'xorg-input-abi-20'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

travis@travis-Lenovo-S21e-20:~$ sudo apt-get install xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

------

Edit: I also tried installing a few other programs while I try to resolve this issue. When installing Steam I encountered this error: 

Steam needs to install these additional packages: 
	libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for travis: 
.................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.5)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 



------


Besides  this I've also installed Synaptics Package Manager to try and filter  out the broken packages, but nothing appears there. I'm very new Linux,  so is there another way to try and identify these broken packages? 

Otherwise  this is a fresh install of Ubuntu, the only edits I've made is to get  new firmware (?) to make my Broadcom network adapter function. 

Thanks in advance for any suggestions

---

### Post by danang2 on 2015-10-24
can you check here? 

[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)

[http://askubuntu.com/questions/251116/why-cant-i-install-these-packages](http://askubuntu.com/questions/251116/why-cant-i-install-these-packages)

[http://askubuntu.com/questions/76766/how-do-i-overcome-these-package-dependency-problems](http://askubuntu.com/questions/76766/how-do-i-overcome-these-package-dependency-problems)

hope help you

---

