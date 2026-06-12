---
title: "How to choose and install proprietary Radeon 7000 / Radeon VE drivers"
date: 2015-01-10
forum: New to Ubuntu
---

### Post by mark187 on 2015-01-10
I have a computer with a K7 Athlon CPU, 1 GB of RAM, and sufficient hard drive space.
I recognize that I won't get flash video. I'm wondering what I might get in the way of HTML5 video, but this is my first serious venture into the Linux world.

I have Lubuntu 14.04.1 LTS installed and have tried to install the proprietary AMD graphics drivers, but I think I have the wrong package or perhaps there are no drivers available for my graphics adapter.

I got to a point where the AMD Catalyst Proprietary Driver 14.501.1003 setup offers to generate a Distribution Specific Driver Package (Recommended) and/or (I'm not sure if I need to do both) to Install Driver 14.501.1003 on X.Org 6.9 or later. I can't get past the point as I get errors for both options.

1. Generate driver results in: "There were errors during package generation. Details... in log."
Log results are rather big, I think. I'm not sure if it's helpful to put that much information here.

Here is just the beginning of the log.[INDENT=2]NOTE: If your system has logged the missing packages required for installation, install them in the order as per the log file to resolve package-dependency issues.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 296: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:14.501-0ubuntu1
dpkg-buildpackage: source distribution trusty
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.BAtoTH
dpkg-buildpackage: host architecture i386
 debian/rules build
#Create important strings
for i in 10fglrx \
[/INDENT]

2. "Install Driver 14.501.1003 on X.Org 6.9 or later" results in "Your Graphics adapter is not supported by this driver. Installation will not proceed."

I've been to [http://support.amd.com/en-us/download](http://support.amd.com/en-us/download), but the manual driver selection process doesn't seem to show Linux drivers. Am I out of luck?

---

### Post by DuckHook on 2015-01-11
Hi mark187 and welcome to Ubuntu and the forums,

I'm afraid that you are out of luck on the proprietary side of things and should not waste any more time trying to build a driver. AMD stopped supporting anything older than the HD series, and even some of the earlier HD cards are no longer supported either. I don't have anything as old as the Radeon 7000 to test out, but I would think that the FOSS driver works with it. Perversely, the FOSS driver is actually called *radeon*, though I thought this name was trademarked by AMD. In any case, AMD has left support of their old cards entirely to the Linux community, although they have recently re-engaged more fully with the community to supply specs and knowledge.

The open source driver has actually come a long way from when it first started and is now a very decent one. I have used both drivers on my AMD card and I'm really impressed with *radeon*. In fact, I prefer it because I know there will be less chance of breakage on updates and upgrades, but then, I'm not a gamer who requires every last ounce of performance out of the thing. Your CPU and card are so old as to be incapable of gaming anyway, so this should not be a consideration.

Bottom line: if you want to run a current, properly patched and secure distro, you have no choice in the matter and will have to stick with the open source driver.

---

