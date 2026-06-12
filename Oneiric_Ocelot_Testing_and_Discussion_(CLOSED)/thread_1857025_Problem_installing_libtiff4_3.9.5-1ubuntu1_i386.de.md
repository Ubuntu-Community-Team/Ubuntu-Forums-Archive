---
title: "Problem installing libtiff4_3.9.5-1ubuntu1_i386.deb on a 64bits system"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mionescu on 2011-10-09
I am using the 64bits of Oneiric beta with the latest updates (as of September 9). I can not install any of the 386 applications (e.g. skype and Acrobat reader). When I try to install either skype of acroread I receive the following error message:

E: /var/cache/apt/archives/libtiff4_3.9.5-1ubuntu1_i386.deb: './usr/share/doc/libtiff4/README' is different from the same file on the system

Any idea how I can fix this?
Thanks.

---

### Post by IWantFroyo on 2011-10-09
Did you install ia32 or use --force-architecture?

---

### Post by mionescu on 2011-10-09
I do have ia32 libs installed and I tried to use --force-architecture without any luck. I still receive the same error. My understanding was that installing 32bits apps on 64bits systems should be easier on Oneiric. One more thing; I updated the system and I did not install it fresh.

---

### Post by IWantFroyo on 2011-10-09
That's what I thought. An update probably broke it. Does purging and reinstalling ia32 help?

---

### Post by mionescu on 2011-10-09
Not, it did not help. After purging ia32 libs, skype, acroread, and all their dependencies, I tried to reinstall skype (with dependencies libqtgui4:i386, libqt4-declerative:i386, sni-qt:i386, libdbusmenu-qt2:i386, and libtiff4:i386). I still receive the same error. The problem seems to be libtiff4:i386. If I install the other dependencies one by one, they install just fine. I receive the error only when I try to install libtiff4:i386.

---

### Post by IWantFroyo on 2011-10-09
```
sudo apt-get install -f
```?

---

### Post by mionescu on 2011-10-09
I did try:
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libtiff4:i386
The following NEW packages will be installed:
  libtiff4:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/143 kB of archives.
After this operation, 541 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 293939 files and directories currently installed.)
Unpacking libtiff4:i386 (from .../libtiff4_3.9.5-1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libtiff4_3.9.5-1ubuntu1_i386.deb (--unpack):
 './usr/share/doc/libtiff4/README' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libtiff4_3.9.5-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks for your help.

---

### Post by IWantFroyo on 2011-10-09
You could download libtiff [here]("http://packages.debian.org/sid/graphics/libtiff-tools") and try to force it.

---

### Post by mionescu on 2011-10-09
I don't really want to mix and match packages from Debian and Ubuntu. I am afraid I will get in more troubles later on. I tried purging every i386 package from the system and reinstall skype. Still no luck.

---

### Post by IWantFroyo on 2011-10-09
You can opt to install libtiff from Synaptic and only download the files. I'm not sure where they go or if there's a DEB, but if you find it, you'll be able to use dpkg arguments on it.

---

### Post by mionescu on 2011-10-09
I managed to solve the problem. In case someone else goes through these problems, here is what I did: I reinstalled libtiff (the 64bits version) and then installed the 32bits version of libtiff and everything installed just fine.

---

### Post by glenstewart on 2011-10-11
> **mionescu said:**
> I managed to solve the problem. In case someone else goes through these problems, here is what I did: I reinstalled libtiff (the 64bits version) and then installed the 32bits version of libtiff and everything installed just fine.

Thank you.  I can confirm this worked for me also.

---

