---
title: "Installing VMware Server in Ubuntu 7.10"
date: 2007-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Zelut on 2007-10-29
This tutorial was sourced from the [Ubuntu Tutorials]("http://ubuntu-tutorials.com") website and ported to the Ubuntu Forums based on its popularity.  For more similar tutorials [visit the website]("http://ubuntu-tutorials.com").

**Installing VMware Server on Ubuntu 7.10**

[LIST=1]
[*][Download VMware Server]("http://vmware.com/download/server/") source from the VMware website.
[*][Download this installer patch]("http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update113.tar.gz"). (source reference)
[*]Extract all the archives to some location on your system (tar -zxvf VMware-server* ; tar -zxvf vmware*)
[*]Ensure that you have [build-essential]("apt:build-essential") installed in order to compile these sources (sudo aptitude install build-essential)
[*]Install the [xinetd]("apt:xinetd") server (sudo aptitude install xinetd)
[*]Run sudo ./vmware-install.pl located within the vmware-server-* unpacked archive.
[*]Select all the default options *EXCEPT* do not compile the modules at this point. (Do you want this program to try to build the vmmon module for your system? NO)
[*]Run sudo ./runme.pl located within the vmware-any* archive. This will launch step 8.
[*]Select the default options and this time answer YES to compile the proper modules.
[*]Run vmware-server using the command vmware or via your Applications Menu.
[/LIST]

---

### Post by SilverWave on 2007-10-30
No need for the patch.
See: HOWTO: Setup VMware Server 1.0.4 on Gutsy (3 Steps, no fuss)
[http://ubuntuforums.org/showthread.php?p=3639728](http://ubuntuforums.org/showthread.php?p=3639728)

---

