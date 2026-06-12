---
title: "[SOLVED] apt-get not installing my ppa packages"
date: 2008-08-27
forum: Packaging and Compiling Programs
---

### Post by Mr. Echo on 2008-08-27
I'm trying to package an upstream version of the zaptel package for my own use in hardy.  I'm calling it zaptel-1.4.12~ppa1.  It's based on the current svn which is soon to be released as 1.4.12.  Anyway, I have successfully built the package with PPA and it was apparently put into my ppa archive.  I never received a "success" email but the build log shows that everything worked.

I've modified my sources.list to point to my ppa and I ran apt-get update.  When I run "apt-get install zaptel" it wants to install the 1.4.10~dfsg-1 that shipped with hardy instead.  Is there something wrong with my new version number that keeps apt-get from seeing it as a newer package?

I'm pretty new to the Ubuntu/Debian world after spending years in Gentoo.  Any help would be appreciated.

---

### Post by Stemp on 2008-08-27
PPA are sometimes slow. You need to wait to see the packages in your pool.
Run an another apt-get update / install to check
If it still doesn't work, give your PPA adress.

---

### Post by Mr. Echo on 2008-08-27
I know PPA is a little slow but some of my tests were built several days ago and I still haven't seen a "successful build" email yet for any of them.

Here's the address of my ppa:

deb [http://ppa.launchpad.net/gentlec/ubuntu](http://ppa.launchpad.net/gentlec/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/gentlec/ubuntu](http://ppa.launchpad.net/gentlec/ubuntu) hardy main

---

### Post by Stemp on 2008-08-27
Your version is **1.4.12~ppa6** while the «old» one is **1:1.4.10~dfsg-1**

---

### Post by Mr. Echo on 2008-08-27
Shouldn't it see 1.4.10 as being older than 1.4.12?  So, is it the 1: that's making the difference here?

---

### Post by Stemp on 2008-08-27
Yes it's not 1.4.10 it's 1:1.4.10.
Look at the debian/changelog file :
zaptel (1:1.4.10~dfsg-1) unstable; urgency=low
and **not**
zaptel (1.4.10~dfsg-1) unstable; urgency=low

---

### Post by Mr. Echo on 2008-08-27
I changed the package version from 1.4.12~ppa7 to 1:1.4.12~ppa7 and it looks like that fixed it.  Thanks for your help!

---

### Post by Stemp on 2008-08-28
You're welcome.

---

