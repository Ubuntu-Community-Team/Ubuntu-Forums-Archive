---
title: "A snap question"
date: 2020-10-12
forum: Packaging and Compiling Programs
---

### Post by kentaylor2525 on 2020-10-12
I did not find a subforum for SNAP so I am posting my question here. If there is a better place, please moderators feel free to move it.

I have found that gnome-commander will not build on Ubuntu 20.04 nor on CentOS 8. Yesterday, while testing a new external hard drive on an Ubuntu 20.04 machine I happened to run df -h. I found a BUNCH of /dev/loop file systems. They were related to snap. This got me looking into the snap "thing." In theory snap will create and mount a virtual file system with the program of interest along with all of its dependencies. This sounded like a path forward for gnome-commander. If I could build the snap on Ubuntu 18.04 - where the program will build, install and run - I could run the snap on a newer version of the OS. I found this excellent reference [http://https://ubuntu.com/tutorials/create-your-first-snap#1-overview](http://https://ubuntu.com/tutorials/create-your-first-snap#1-overview)

I followed the instructions and created my snapcraft.yaml (configuration) file thus:

name: gnome-commander-snap
base: core18
version: 1-10-3
summary: gnome-commander in a snap
description: thie is my gnome-commander first snap attempt
grade: devel # must be 'stable' to release into candidate/stable channels
confinement: devmode # use 'strict' once you have the right plugs and slots
parts:
gnome-commander:
source: [https://ftp.gnome.org/pub/GNOME/sources/gnome-commander/1.10/gnome-commander-1.10.3.tar.xz](https://ftp.gnome.org/pub/GNOME/sources/gnome-commander/1.10/gnome-commander-1.10.3.tar.xz)
plugin: autotools

When I attempted to run the snap making process I received this error:

Failed to run './configure --prefix=' for 'gnome-commander': Exited with code 1.
Verify that the part is using the correct parameters and try again.
Run the same command again with --debug to shell into the environment if you wish to introspect this failure.

I then ran snapcraft --debug which told me:

checking for itstool... no
configure: error: itstool not found

However:

ken@t15:~/Desktop/mysnaps/gnome-commander$ sudo apt-get install itstool
Reading package lists... Done
Building dependency tree
Reading state information... Done
itstool is already the newest version (2.0.2-3.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am currently stuck. I can run ./configure and everything seems to check out OK. I have not yet run make but I suspect that it will be OK as I have done so before on Ubuntu 18.04.  Any advice would be greatly appreciated.

TIA,

Ken

---

