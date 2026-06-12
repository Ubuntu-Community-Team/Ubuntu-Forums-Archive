---
title: "libqt dependency"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by stonecoldjha on 2012-02-26
Hi,
I installed lubuntu 11.10, and proceeded to install virtualbox (using the deb file for 11.10 downloaded from oracle's site), but gdebi package manager fails saying some libqt-network dependency not satisfiable. I removed everything starting wth libqt from synaptic, but still cannot get it to install. How do I fix it?

---

### Post by stonecoldjha on 2012-02-26
I went through [https://forums.virtualbox.org/viewtopic.php?f=7&t=45469](https://forums.virtualbox.org/viewtopic.php?f=7&t=45469)
and ran     sudo apt-get install dkms build-essential linux-headers-generic .....but i got the following output:

sonu@sonu-desktop:~$ sudo apt-get install dkms build-essential linux-headers-generic
[sudo] password for sonu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dkms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'dkms' has no installation candidate
E: Package 'build-essential' has no installation candidate

what does this package <x> has no installation candidate mean?

---

### Post by Lisiano on 2012-02-26
It means that some package wants/depends on that package but such a package doesn't exist. Try updating 
```
sudo apt-get update
```
Also virtualbox is in the Ubuntu repository, so you can just install it from there and all it's dependencies
```
sudo apt-get install virtualbox
```
It's a bit outdated, (Currently at 4.1.2 when 4.1.8 is out) so if you wish to use the latest, you can add this PPA
```
sudo add-apt-repository ppa:debfx/virtualbox
sudo apt-get update
sudo apt-get install virtualbox
```

---

### Post by stonecoldjha on 2012-02-27
I did sudo apt-get update..and it started downloading package information...but after some time I got:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFB4FA7E41D78D0C
E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index (1)
sonu@sonu-desktop:~$ 
what do i do now?

---

