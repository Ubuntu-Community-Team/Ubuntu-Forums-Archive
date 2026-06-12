---
title: "[SOLVED] Download Package and Dependencies"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by wormser on 2008-10-29
I want to download a package and install it on another computer.  The problem is there are a lot of dependencies.  How can I download a package and its dependencies without having to keep going through the dependencies tree.  Is there a way to download a package and its dependencies easily.  I am looking to download madwifi for Ibex and I am running Gusty on the computer connected to the internet.

Thanks.

---

### Post by arochester on 2008-10-29
APTonCD? [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by wormser on 2008-10-29
Great idea, but they do not have Ibex yet.  Any other ideas?

---

### Post by igknighted on 2008-10-29
> **wormser said:**
> Great idea, but they do not have Ibex yet.  Any other ideas?

if you use apt-get --help there is a flag you can use to download all the packages that would need to be installed, but not install them.  You could then grab all those packages and manually install them on the other system.  I'd look up what that flag is but I'm on Windows at the moment and for some reason when I pull up the terminal 'apt-get' doesn't work...

---

### Post by ajgreeny on 2008-10-29
The easiest way would be to run the installed or even the live CD version of 8.10, and using synaptic, generate the script file you need to download the packages plus dependencies to a usb drive.  You can then simply install these packages from the usb drive to the other non-connected computer by double clicking on them, or if that causes problems due to the order of installing, navigate to the usb drive in terminal and use ```
sudo dpkg -i *.deb
```That should do it easily.

---

### Post by forger on 2008-10-29
So the computer on the internet has gutsy, and you need madwifi for ibex.. hm.. ethernet cable is out of the question? :D

1) pbuilder - instead of using it to package stuff, you can use it to download your apt packages, e.g. you issue a command within the package builder system:
```
sudo apt-get install madwifi-tools
```

Now you know exactly with dependencies you need, since apt-get shows you all the packages required to be installed!

Info on how to install pbuilder: [https://wiki.ubuntu.com/PackagingGuide/Intro/Pbuilder](https://wiki.ubuntu.com/PackagingGuide/Intro/Pbuilder)
e.g. to build an intrepid pbuilder "machine":
**[COLOR="Red"]WARNING! Not tested, use at your own risk![/COLOR]**
```
sudo apt-get install pbuilder
sudo pbuilder create --distribution intrepid --othermirror "deb http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse"
```

Too much to read, but also quite good and clean, since every time you exit the pbuilder "machine" pbuilder gets back to its original state :)
It might also be wise to install ubuntu-desktop or something.

2) easier, use [http://packages.ubuntu.com/madwifi](http://packages.ubuntu.com/madwifi) to search for the dependencies.
If you have a local install of intrepid, you can output a list with its already installed packages.
a) execute this command on the intrepid machine:
```
dpkg -l | grep '^ii' | tr -s ' ' | cut -d ' ' -f 2,3 > $HOME/Desktop/packages.txt
```

Once you issue this command it will create a **packages.txt** file
b) Transfer packages.txt to the gutsy machine (with the internet).

c) Every time you look for a dependency at [http://packages.ubuntu.com]("http://packages.ubuntu.com"), you open the text file and search inside for the name of the package. If you have it, you move on to the next dependency etc.

This way is rather easy, but painful to the time wasted :)

---

### Post by igknighted on 2008-10-29
Wait, doesn't Ibex come with Ath5k and Ath9k preinstalled?  These drivers replaced madwifi, I don't think you need it anymore.

---

### Post by forger on 2008-10-29
ath9k in linux-image-2.6.27-7-generic
$ modinfo ath9k
filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5307204F68EC6FC867B1E91
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        mac80211
vermagic:       2.6.27-7-generic SMP mod_unload modversions 


ath5k is in the linux-headers-2.6.27-7 though

---

### Post by wormser on 2008-10-29
> **igknighted said:**
> Wait, doesn't Ibex come with Ath5k and Ath9k preinstalled?  These drivers replaced madwifi, I don't think you need it anymore.

You are right.  I got it working!  When I first tried I had 2 wireless cards in and it did not work.  I just plugged in the Proxim card by itself and it worked.  Thanks for all the replies.

---

