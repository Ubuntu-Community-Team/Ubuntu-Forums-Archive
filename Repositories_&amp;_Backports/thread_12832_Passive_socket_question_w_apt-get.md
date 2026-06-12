---
title: "Passive socket question w/ apt-get"
date: 2005-01-27
forum: Repositories &amp; Backports
---

### Post by herting on 2005-01-27
Hello all, wanted to begin by saying thanks.  I just started using Ubuntu on my laptop 4 days ago and am now working on switching all my other computers to it because I am so pleased with the product.  

But I also have an issue which I suspect might be easily resolvable, given that the person working on it is anyone but me.

I am behind an impressively strict firewall currently (living on campus currently) and as such, only have a handful of usable ports.  One of the things that I can't do behind this firewall is have a passive socket ftp connection.

This inhibits my ability to pull from some of the ftp based apt-get repositories like nerim.net.  

Is there any way I can change the settings in my sources.list file to specify no passive connections?  If no, any other solution to this problem, or even just suggesting a few http-based repositories that contain similar content would make my life much easier.

Thanking you in advance for any help I can get here, and in reflection for the very impressive distribution.

*Update:*

Not sure if this will help, but here is what happens when I try to install a package from some repositories:
> keith@britebox:~ $       sudo apt-get install libdvdcss2
Reading Package Lists... Done
Building Dependency Tree... Done
The following NEW packages will be installed:
  libdvdcss2
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 26.7kB of archives.
After unpacking 106kB of additional disk space will be used.
Get:1 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main libdvdcss2 1.2.8-0.0 [26.7kB]
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main libdvdcss2 1.2.8-0.0
  Could not connect passive socket.
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb)  Could not connect passive socket.
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

