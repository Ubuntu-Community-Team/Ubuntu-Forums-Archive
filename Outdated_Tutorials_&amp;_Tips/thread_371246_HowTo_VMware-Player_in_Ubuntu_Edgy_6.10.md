---
title: "HowTo: VMware-Player in Ubuntu Edgy 6.10"
date: 2007-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by radiohead on 2007-02-26
THIS IS TO COMPILE VMPLAYER FROM THE REPOS!!!!

I have been working on vmware for about a year, and when I formatted and upgraded to edgy, vmware-player wouldn't install, and apt-get source wouldn't compile either, but I found a way around it (at least to compile it anyway :-P). It's a bit hackish, but it works all the same.

First off, the package in the repos is broken and doesn't contain the vmmon and vmnet tarballs that you need, so you can get them with this.

```

wget http://76.186.170.17/radiohead/Desktop/vmmon.tar
wget http://76.186.170.17/radiohead/Desktop/vmnet.tar

sudo mkdir /usr/lib/vmware/modules/source
sudo cp ./vm*.tar /usr/lib/vmware/modules/source/

```

Then, we need to get the dependecies for it (which I graciously steal from [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server))

```

sudo apt-get install libx11-6 libx11-dev libxtst6 xlibs-dev xinetd wget linux-headers-`uname -r` build-essential gcc binutils-doc cpp-doc make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1

```

Then, cd to the directory where you source is contained and run the vmware-install.pl script as root and you are good to go.

This was done on 32-bit Edgy.

---

### Post by bryand on 2007-03-15
Call me lazy!, but the easy way to install VMPLAYER is via Synaptic

---

### Post by bethalicea on 2007-03-15
Would you mind explaining how?  I've just installed xubuntu on my laptop cause it can't handle any more than that.  I'm VERY new to ubuntu and I'm having trouble getting the commands to work in the Terminal.  I don't even know which installation I need - tar or rpm!!  Can you help me?

---

### Post by bryand on 2007-03-15
This how to although based on 6.06 should be useful.

[http://help.ubuntu.com/xubuntu/desktopguide/C/add-applications.html](http://help.ubuntu.com/xubuntu/desktopguide/C/add-applications.html)

---

### Post by jms1989 on 2007-03-16
I can't download the tarballs.

Unable to connect to host. Can you upload them to a different host?

---

