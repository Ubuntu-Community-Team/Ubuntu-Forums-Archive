---
title: "Linksys Wireless Card Compatibility"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by nwusr on 2012-03-10
I installed Ubuntu a couple days ago on an old laptop that I recently repaired. The laptop does not have an internal wireless card, I am using a Linksys WPC54G (ver 1). I used ndiswrapper to import the driver and the hardware is recognized. However, when I try to configure the network, no wireless networks appear.

The ndiswrapper wiki (link below) says that some issues can be fixed by adding "acpi=noirq" to the kernel parameters. I have no idea how to do this though. Any help would be appreciated.

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WPC54G](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WPC54G)

p.s. The wireless card does function, I tested it on another laptop that runs XP.

---

### Post by wolfen69 on 2012-03-10
```
gksudo gedit /etc/default/grub
```
then add **acpi=noirq** on it's own line at the bottom of the list. Close and save.
Then do 
```
sudo update-grub
```
reboot.

---

### Post by nwusr on 2012-03-10
Thanks for the response, Wolfen. Between your help and the installation doc in the link below, I finally got it to work.

Thanks!

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

