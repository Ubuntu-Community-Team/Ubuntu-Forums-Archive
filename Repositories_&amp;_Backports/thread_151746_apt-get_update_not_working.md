---
title: "apt-get update not working"
date: 2006-03-28
forum: Repositories &amp; Backports
---

### Post by Maddman on 2006-03-28
I'm trying to get LTSP working on my Breezy server, and I'm having trouble getting the latest packages.  I'm following a How-To for Hoary and kind of figuring it out along the way. - [http://linus.yhspatriot.net/cs/docs/ubuntu_howto/UbuntuLTSPInstall](http://linus.yhspatriot.net/cs/docs/ubuntu_howto/UbuntuLTSPInstall)

I've gotten DHCP working, but still have some more configuration to do.  I don't have xdm installed, so I go to install it.  I got the updater working last week.  When I do apt-get install xdm, I get 

Reading package lists...
Building dependency tree...
The following NEW packages will be installed:
  xdm
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 111kB of archives.
After unpacking 569kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xdm
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe xdm 1:0.99.1-3
  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/x/xdm/xdm_0.99.1-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/x/xdm/xdm_0.99.1-3_i386.deb)  Cannot initiate the connection to 3128:80 (0.0.12.56). - connect (22 Invalid argument)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

So I try sudo apt-get update, and I get the following

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  403 Forbidden
Reading package lists...

It worked last week!  I had to make a change to get through the firewall, where I added the proxy address to the .bashrc file.  I also had to move the sserver to a different IP address, could there be something there that I'm missing?  Nothing funny in my netstat -rn.

Any advice would be deeply appreciated!

---

