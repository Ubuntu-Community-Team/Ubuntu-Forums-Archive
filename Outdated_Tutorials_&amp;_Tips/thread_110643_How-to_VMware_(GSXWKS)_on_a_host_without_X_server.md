---
title: "How-to: VMware (GSX/WKS) on a host without X server"
date: 2005-12-31
forum: Outdated Tutorials &amp; Tips
---

### Post by calt129 on 2005-12-31
Hi ppl,

I'll explain in this post how to install VMware on a stripped down Linux installation without an X server, specifically Ubuntu Server 5.10.

My motivation was simple: "to have as many resources as possible for the VMs". In order to do that the host is trimmed down a bit, i.e. only SSH and xinetd run on the machine and `free -m` shows 13 MB usage. This guide explains the GSX server but I'm quite sure the steps for Workstation version look the same (and ESX doesn't need a host OS anyway).

[LIST=1]
[*]Install your OS first (Ubuntu Breezy server), this gives you an installation without an X server
[*]Upgrade your kernel if necessary:
```
sudo apt-get update upgrade
```
(I'm not sure if this one above updates the kernel) **or** using aptitude
```
sudo aptitude
```
Since VMware compiles a kernel module for your running kernel, you'll have to have the right kernel version at the time of compilation. If you do it afterwards, you'll have to install a new set of kernel-headers.
For more information see: [https://wiki.ubuntu.com/VmWare]("https://wiki.ubuntu.com/VmWare")
[*]Install gcc 3.4 & kernel-headers if necessary:
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 g++-3.4
```
**EDIT:**
It looks you don't need the whole *build-essential* package, *make* suffices as well. So try the following first, if this does not work, use the one above:
```
sudo apt-get install make linux-headers-`uname -r` gcc-3.4 g++-3.4
```
[*]Install xinetd if you use VMware GSX, Workstation users don't need this (GSX installs a daemon for remote connections)
```
sudo apt-get install xinetd
```
[*]Install VMware as usual:
```

cd vmware-gsx-distrib
sudo sh -c 'CC=/usr/bin/gcc-3.4 ./vmware-install.pl'

```
The installer will ask you at some point if you want to run vmware-config.pl, say *yes*.
[*]Now vmware complains about the output of *ldd /usr/local/bin/vmware* and missing dependencies. For each dependency search for the corresponding package and install. This will not install a complete X server but only the required libraries. Although VMware does not necessarily need a GUI, some of the programs are linked against X libraries.

Here's an example. VMware complains about missing "*libX11.so.6*". So if you run:
```
sudo apt-cache search libX11.so.6
```
you get the output:
[INDENT][I]libx11-6 - X11 client-side library
libx11-6-dbg - X11 client-side library (debug package)
libx11-dev - X11 client-side library (development headers)
xlibs-dev - X Window System client library development files transitional package
libx11-freedesktop-desktopentry-perl - perl interface to Freedesktop.org .desktop files
libx11-protocol-perl - Perl module for the X Window System Protocol, version 11[/I][/INDENT]
See the first line? You'll have to find the closest match as possible, in this case *libx11-6*. Then you install it with:
```
sudo apt-get install libX11-6
```
I don't think you'll have more dependencies than my box, but repeat the process for each dependency. I've found these in my ~/.bash_history:
```
sudo apt-cache search libXtst
sudo apt-get install libxtst6
sudo apt-cache search libXt
sudo apt-get install libxt6
sudo apt-cache search libxpm
sudo apt-get install libxpm4
```
A few libraries such as libice will be automatically installed. Funnily though the file */usr/local/bin/vmware* is a Perl script, so you can't run *ldd /usr/local/bin/vmware* it on your own :P Eventually you'll have to break the vmware installation at that point, and re-start the installation until there are no more dependencies.

**EDIT:** There's another warning about outdated libc (*"upgrade your libc5 to glibc"*), you can safely ignore that :)

[*]Now, this might not be an Ubuntu-specific issue, I've experienced it on different distros as well. The problem is this:
You open a new console, open an existing VM (or simply register it with:
```
sudo vmware-cmd -s /path/to/your/vm/myvm.vmx
``` and want to start it. VMware complains about an error with no text! *grrr* No matter what you do, VMware doesn't start the machine.
I've tried starting it as root directly from the command line:
```
sudo vmware-cmd /path/to/your/vm/myvm.vmx start
```
If it does not work, add your user to the list of trusted users with:
```
sudo vmware-authtrusted -e -u myuser
```
Also check if the .vmware directory in **your** home folder is owned by you and not root. If not do a simple
```
sudo chown -fR myuser:myuser ~/.vmware
```
Sometimes the .log files or the .vmx files also might have wrong permissions, please check if you have access to these files. AFAIK, the only file that should be writable is .vmx file, correct me if I'm wrong.
[/LIST]

This should do it. I've included the last step as a bonus, you might not need it. Any corrections, suggestions, free beer welcome :) Peace and out!

---

### Post by p1tst0p on 2006-01-08
excelent how-to, helped me get GSX going on my breezy box

many thanks.

---

