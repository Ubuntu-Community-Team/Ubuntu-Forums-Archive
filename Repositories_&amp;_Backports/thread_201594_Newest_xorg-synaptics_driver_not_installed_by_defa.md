---
title: "Newest xorg-synaptics driver not installed by default"
date: 2006-06-22
forum: Repositories &amp; Backports
---

### Post by nerd65536 on 2006-06-22
Short version:
"xserver-xorg-input-synaptics" is old (0.14.3).  A newer package is available "xfree86-driver-synaptics" (0.14.4), but installing that makes "ksynaptics" uninstall

Someone please update "xserver-xorg-input-synaptics" to the newer version or make "ksynaptics" depend on "xserver-xorg-input-synaptics | xfree86-driver-synaptics"

Or, How do I force ksynaptics to install if I'm using "xfree86-driver-synaptics"?

Long story:

The version of "xserver-xorg-input-synaptics" is "0.14.3+seriouslythistime-0ubuntu3"
There is also a package, "xfree86-driver-synaptics" that is version "0.14.4-1"

"xfree86-driver-synaptics" seems to be the newest version of the driver.  

"ksynaptics" should have at least version "0.14.4" to work properly, but it depends on "xserver-xorg-input-synaptics" (no version specified)



___________________
My configuration:
Kubuntu Dapper x64
sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

---

