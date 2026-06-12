---
title: "[Howto] install qBittorrent"
date: 2009-12-20
forum: Outdated Tutorials &amp; Tips
---

### Post by michael37 on 2009-12-20
**[SIZE="3"]What is it?[/SIZE]**
[INDENT]qBittorrent is the closest open source equivalent to uTorrent available on Ubuntu.  
[LIST]
[*][Official page of qBittorrent.]("http://qbittorrent.sourceforge.net/")  
[*][Read more about qBittorrent.]("http://www.webupd8.org/2009/12/qbittorrent-closest-open-source.html")
[/LIST]
Current version of qBittorrent is version 2.  Version 2.1 is in beta. Version 1.2 is old, and is the only one available for older versions of Ubuntu.[/INDENT]

**[SIZE="3"]Why is this howto here?[/SIZE]**
[INDENT]Because most of the online guides, esp for the older versions of Ubuntu, do not work.  Other online guides have not been updated for version 2 of qBittorrent.
[/INDENT]

**[SIZE="3"]Installation instructions for Jaunty and Karmic.[/SIZE]**
[INDENT]qBittorrent is now available in official Ubuntu repositories since v9.04 Jaunty. Packages are automatically imported from Debian repositories are they are maintained on Ubuntu by Andrew Starr-Bochicchio.  However, Jaunty universe repository provides only version 1.3, and Karmic provides version 1.5.

Modern version 2 of qBittorrent for Jaunty and Karmic is published on author's PPA [here]("https://launchpad.net/~hydr0g3n/+archive/ppa"). To use this PPA with Ubuntu v9.10 Karmic, please use the following command
```
sudo add-apt-repository ppa:hydr0g3n/ppa
```

To use it with Ubuntu v9.04 Jaunty, please add the following lines to your /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu jaunty main
```

This PPA is signed, please get my key by doing this (Jaunty only):
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 47B4D1C4
```

Then install qBittorrent by doing this:
```
sudo apt-get update && sudo apt-get install qbittorrent 
```
[/INDENT]
Source: based on [http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php)

**[SIZE="3"]Installation instructions for Hardy.[/SIZE]**
[INDENT]
Only version 1.2 is available for Hardy users. Add the following lines to your /etc/apt/sources.list:
```
deb http://hydr0g3n.free.fr/ubuntu/ hardy main
deb-src http://hydr0g3n.free.fr/ubuntu/ hardy main
```

This PPA is signed, please get my key by doing this:
```
sudo apt-key adv --keyserver wwwkeys.pgp.net --recv-keys A08A9A43
```

Then install qBittorrent by doing this:
```
sudo apt-get update && sudo apt-get install qbittorrent 
```
[/INDENT]

---

