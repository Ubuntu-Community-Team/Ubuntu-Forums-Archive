---
title: "Broken package overwriting file that also exists in another package"
date: 2005-02-20
forum: Repositories &amp; Backports
---

### Post by m3ta on 2005-02-20
This is EXACTLY the reason why i dumped Debian-Sid in the first place: bad management of the so-called 'new' packages.
Doesn't anyone actually TEST the stuff that gets into the reps?


Preparing to replace kdelibs-data 4:3.3.2-1ubuntu6 (using .../kdelibs-data_4%3a3.3.2-1ubuntu7_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.3.2-1ubuntu7_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/applications.menu', which is also in package gnome-menus
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.3.2-1ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
dpkg: dependency problems prevent configuration of kdelibs:
 kdelibs depends on kdelibs-data (>= 4:3.3.2-1ubuntu7); however:
  Version of kdelibs-data on system is 4:3.3.2-1ubuntu6.
dpkg: error processing kdelibs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdelibs
Reading Package Lists... Done             
Building Dependency Tree       
Reading extended state information      
Initializing package states... Done

---

### Post by kassetra on 2005-02-20
kde is in the "universe" repositories, which, as explicitly stated on the ubuntu web site are not maintained by the ubuntu team.
 
 Please see the documentation, [here]("http://www.ubuntulinux.org/support/documentation/faq/kde").
 
 As for your problem, try this:
 ```
dpkg -i --force-depends-version gnome-menus_2.9.90-0ubuntu1_i386.deb
```
 and then this:
 ```
apt-get install libgnome-menu0
```

---

### Post by Yukonjack on 2005-02-20
[QUOTE=m3ta]This is EXACTLY the reason why i dumped Debian-Sid in the first place: bad management of the so-called 'new' packages.
Doesn't anyone actually TEST the stuff that gets into the reps?
[/QUOTE]

You should not have been running Sid in the first place unless you want to help with testing sid is the unstable branch of Debian in other words use at your own risk, they clearly point that out on their web site. If you want Debian stable it's Woody and Sarge will be coming up for the Debian stable soon.
As for your problem here what are you running Warty or Hoary?

---

