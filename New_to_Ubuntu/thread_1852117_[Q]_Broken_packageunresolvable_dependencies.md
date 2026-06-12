---
title: "[Q] Broken package/unresolvable dependencies"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by dzchimp on 2011-09-29
Natty Narwhal->Running on 16GB USB Key
Trying to install kompare


```
$ sudo apt-get install kompare
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kompare : Depends: kdebase-runtime but it is not going to be installed
           Depends: libkde3support4 (>= 4:4.3.4) but it is not going to be installed
           Depends: libkdeui5 (>= 4:4.3.4) but it is not going to be installed
           Depends: libkio5 (>= 4:4.3.4) but it is not going to be installed
           Depends: libkparts4 (>= 4:4.5.80) but it is not going to be installed
           Depends: libktexteditor4 (>= 4:4.3.4) but it is not going to be installed
           Depends: libqt4-qt3support (>= 4:4.5.3) but it is not going to be installed
E: Broken packages
```

What do I do? I've tried the following in an attempt to fix, but didnt work:

```
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*; sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists; sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean; sudo apt-get autoclean
sudo apt-get update
sudo dpkg --clear-avail; sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by acrazyplayer on 2011-09-30
apt-get is great for certain things but it fails at harder things because it is trying to keep your system stable.

use aptitude instead. you may have to install it so do 

"sudo apt-get install aptitude" 

then do "sudo aptitude update && sudo aptitude install kompare"

it will probably give you some choices of what to remove and what to install, if what it says is not what you want then push "n" and it will try another way, keep doing this until it says what you want it to do. If it keeps saying the same stuff  and it still is not what you want then you need to try to find another way to install the packages you want.

---

### Post by Rex Bouwense on 2011-09-30
I would use Synaptic Package Manager.  When you try to install a package it will also install or tell you that dependencies must also be installed.  That makes it easy, for me anyway.

---

