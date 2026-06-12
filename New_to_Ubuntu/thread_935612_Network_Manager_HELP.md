---
title: "Network Manager HELP"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Macrosystems on 2008-10-01
Sorry if this is in the wrong section...
Someone suggested I install a new network manager (wicd) in order to access networks with hidden SSIDs. I was unaware that installing this new manager would uninstall my default manager. Now I cannot access the internet and I'm stuck with a broken network manager. I tried downloading the network deb files but I'm not sure which ones I need or how to install them.
Please help!

---

### Post by DagMan on 2008-10-01
you need the packages
network-manager
network-manager-gnome
The .deb files I mean
once you have them in on your hard drive, go to the terminal
```
sudo apt-get remove wicd
```
then install the other 2 packages starting with network-manager and then network-manager-gnome by double clicking the files, or if you want to use the command line
```
sudo dpkg -i network-manager*deb
```


You can download the files needed by searching and following the links here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Just be sure to choose the right Ubuntu version and the right architecture, 32 or 64 bit, when there are differant links for the two.

Edit: Sorry, changed apt-get to dpkg for installing at the command line

---

