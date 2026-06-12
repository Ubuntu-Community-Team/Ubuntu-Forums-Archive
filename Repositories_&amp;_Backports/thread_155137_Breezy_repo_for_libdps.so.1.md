---
title: "Breezy repo for libdps.so.1"
date: 2006-04-04
forum: Repositories &amp; Backports
---

### Post by jmb365 on 2006-04-04
Hi,

I am trying to find a library module libdps.so.1 for "Breezy" for a software that needs this.  It seems to be available for "Hoary" but not in "Breezy".

Has this been dropped, replaced or backported?  Can somebody shed any light?

A Google search did seem to help.  I tried "apt-file search libdp"  but got nowhere...

Thanks
JMB

I found my own answer.  The fix is to get Hoary's libdps1 package, since a Breezy package is not available.  The steps are:
cd /tmp
wget -nd [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/libdps1_6.8.2-10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/libdps1_6.8.2-10.1_i386.deb)
sudo dpkg -i libdps1_6.8.2-10.1_i386.deb

---

