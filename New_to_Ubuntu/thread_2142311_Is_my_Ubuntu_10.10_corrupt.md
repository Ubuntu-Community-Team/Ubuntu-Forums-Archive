---
title: "Is my Ubuntu 10.10 corrupt?"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by msinfo on 2013-05-05
Hi, 

Today I was trying to install few, programs, but because of error message - "Requires installation of untrusted packages", I could not install any.This happened for python idle3, when i tried sudo apt-get install idle, it went perfectly with message, that some packages couldn't be installed. When I tried to launch it, it failed stating such program is not installed.

This happened with other programs too.
When I try to update my Ubuntu, to latest release, I saw error message - "Failed to download repository information". I saw following in details.

:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.201 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.201 80]

and many more.

Note: Also, when this question gets solved, how do I mark it as solved? Because I could not found any option for doing that, in my last two question, because of changes occurring in interface of forums.

Kindly guide me.

Thanking you.

---

### Post by ibjsb4 on 2013-05-05
10.10 reached EOL a year ago.  Time to move on :)

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by msinfo on 2013-05-05
So how do I update my system now, without re-installing Ubuntu.

---

### Post by ibjsb4 on 2013-05-05
Really should do a fresh install in this case as you will need to upgrade to 11.04 next and thats EOL, then 11.10, then 12.04.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=eol+old+release+upgrade&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%3Au-ocqbntw_o%26q%3Dupgrade%2Bold%2Brelease%26sa%3DSearch%26cof%3DFORID%3A9](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=eol+old+release+upgrade&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%3Au-ocqbntw_o%26q%3Dupgrade%2Bold%2Brelease%26sa%3DSearch%26cof%3DFORID%3A9)

---

### Post by msinfo on 2013-05-05
Thanks ibjsb4 for info. 
Currently I am upgrading to 11.04, using help from Help file topic : How can I upgrade to the latest version of Ubuntu?
and command  update-manager -c -d. It's under process.
But can I know, what makes it to fail install python idle3 via Ubuntu Software Centre or command line. This not only happens with idle but with others software's too which I want to install.

---

### Post by ibjsb4 on 2013-05-05
> Currently I am upgrading to 11.04

Post back when your 11.04 upgrade is complete, let us know how it went.

> How can I upgrade to the latest version of Ubuntu?

Next is 11.10 and then your one step away from 12o4 LTS, supported till 2017 :)

---

### Post by fantab on 2013-05-05
> **msinfo said:**
> 
Currently I am upgrading to 11.04

Really, you must do a Clean install of the latest version available, ie 12.04 or 13.04. It will save you both time and other possible headaches...

---

### Post by codingman on 2013-05-05
Doing a clean install really is a better idea than going up the versions, one-by-one, especially if your version has reached EOL. This will result in a tangled mess of repositories and other packages, so it's worth the trouble of burning a disc over migraines.

---

### Post by 3rdalbum on 2013-05-05
You can't go up to 11.04 either, it's also well and truly out of support.

A clean install is now the only way, you've left it too long to do an in-place upgrade.

These days you can do a clean install while retaining your home folder (even if it's in the same partition as /). It's really very easy.

---

### Post by BluNova on 2013-05-05
> **3rdalbum said:**
> 
These days you can do a clean install while retaining your home folder (even if it's in the same partition as /). It's really very easy.
Really? i thought you had to format it oh well.

You really should just do a clean install though, upgrades are never pretty

---

