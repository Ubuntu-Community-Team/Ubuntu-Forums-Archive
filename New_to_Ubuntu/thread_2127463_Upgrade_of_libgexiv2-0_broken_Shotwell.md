---
title: "Upgrade of libgexiv2-0 broken Shotwell"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by serfcx on 2013-03-20
I have yorba's PPA activated and the recent upgrade of libgexiv2-0 to 2-1 has broken Shotwell 0.14.
Should I downgrade to 2-0 ?
According to the yorba site is should still work with 2-1. Confused :confused:

Edit Sorry should have said using U 12.04 LTS

---

### Post by rabicula on 2013-03-20
Hello,

I didn't have any yorba ppa and my 12.04 dist-upgrade just removed shotwell and there's no way to install it back,

```
mizuki ~ # apt-get install shotwell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 shotwell : Depends: libgstreamer-plugins-base1.0-0 (>= 1.0.0) but it is not installable
            Depends: libgstreamer1.0-0 (>= 1.0.0) but it is not installable
E: Unable to correct problems, you have held broken packages.apt-get install shotwell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 shotwell : Depends: libgstreamer-plugins-base1.0-0 (>= 1.0.0) but it is not installable
            Depends: libgstreamer1.0-0 (>= 1.0.0) but it is not installable
E: Unable to correct problems, you have held broken packages
```

---

### Post by chamcha on 2013-03-20
Hello,

I had the same issue with 12.04 and Yorba PPA installed.

As a workaround, I downloaded and installed the two following packages from Ubuntu Raring Packages web site ([http://packages.ubuntu.com](http://packages.ubuntu.com)) :
- libgstreamer1.0-0_1.0.5-1ubuntu1_i386
- libgstreamer-plugins-base1.0-0_1.0.5-1_i386

I was then able to install shotwell and everything seems to work properly so far.

---

### Post by serfcx on 2013-03-20
> **chamcha said:**
> Hello,

I had the same issue with 12.04 and Yorba PPA installed.

As a workaround, I downloaded and installed the two following packages from Ubuntu Raring Packages web site ([http://packages.ubuntu.com](http://packages.ubuntu.com)) :
- libgstreamer1.0-0_1.0.5-1ubuntu1_i386
- libgstreamer-plugins-base1.0-0_1.0.5-1_i386

I was then able to install shotwell and everything seems to work properly so far.

Thanks a lot chamcha, works for me too :)

---

