---
title: "Wine -  error - no package header"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by Loki*PI on 2013-06-06
**Resolution:  **
tracking down the error messages I found two files that seem to be incomplete or corrupted 
/var/lib/apt/lists
	ubuntu-ashisuto.ubuntulinux.jp_ubuntu_dists_raring-updates_universe_binary-i386_Packages
	ubuntu-ashisuto.ubuntulinux.jp_ubuntu_dists_raring-security_main_binary-i386_Packages

I changed the name of the two files and then was able to run apt-get purge wine.  This seems to have clear the system. The error icon is gone, and I'm able to run apt-get, synaptic, and software center. 

I am also changing my source server.


**Original problem:    ** 

Hi:  I tried to install Wine on 13.04 using synaptic and got an incomplete install. Synaptic keeps trying to complete the installation and generates the following error:

E: Encountered a section with no Package: header, 
E: Problem with MergeList /var/lib/apt/lists/ubuntu-ashisuto.ubuntulinux.jp_ubuntu_dists_raring-updates_universe_binary-i386_Packages, 
E: The package lists or status file could not be parsed or opened.

Notice says this is serious and to report it, I don't really know where to report this so could someone send this to the people who need to know.

This has knocked out both synaptic and software center, neither will run. I tried to remove Wine with apt-get but that won't run either.  Any suggestions on how to clear my system?

Thanks

---

