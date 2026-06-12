---
title: "dependent Packages"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Spgt on 2013-02-17
Hi,

I am trying to install Ace stream(.deb) on ubuntu 12.10 and it seems that I have some dependencies. So I am going to walk you thorough what I have done so far 

1- sudo apt-get update
2- sudo dpkg -i (filename)

/////////////////////////////////////////
Unpacking replacement torrentstream ...
dpkg: dependency problems prevent configuration of torrentstream:
 torrentstream depends on libupnp3 (>= 1.4.3); however:
  Package libupnp3 is not installed.
 torrentstream depends on libva-x11-1 (>> 1.0.12~); however:
  Package libva-x11-1 is not installed.
 torrentstream depends on libvcdinfo0 (>> 0.7.23); however:
  Package libvcdinfo0 is not installed.
 torrentstream depends on libx264-116 | libx264-120; however:
  Package libx264-116 is not installed.
  Package libx264-120 is not installed.

dpkg: error processing torrentstream (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 torrentstream
/////////////////////////////////////////

Then I installed gdebi
3- sudo gdebi (file name)
//////////////////////////////////////////
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 
This package is uninstallable
Dependency is not satisfiable: libupnp3 (>= 1.4.3)
////////////////////////////////////////////


So I decide to download the package from 

[http://packages.debian.org/sid/libupnp3](http://packages.debian.org/sid/libupnp3)

and when I used dpkg commend it was still dependent on some other packages that I didn't have! 
It is like an endless loop!

WHAT THE HELL SHOULD I DO? :P

---

### Post by schragge on 2013-02-17
Follow [this how-to]("http://wiki.acestream.org/wiki/index.php/Streaming/en#Installing_ACE_Stream_on_Debian.2FUbuntu_from_repository").

> **Spgt said:**
> 
So I decide to download the package from [http://packages.debian.org/sid/libupnp3](http://packages.debian.org/sid/libupnp3)
You're using Ubuntu 12.10, but trying to install a package from *Debian sid*. This may not work.

---

### Post by Spgt on 2013-02-17
It worked!

Thanks

---

