---
title: "Update on (26/08/2011) breaks ia32-libs and I can't use Android SDK because of this"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jucas_lo on 2011-08-26
As the title says Update on (26/08/2011) breaks ia32-libs and I can't use Android SDK because of this.

ia32-libs depends on lib32v4l-0, but this package cannot be installed:

```
lib32v4l-0 : Depends: libv4l-0 (= 0.8.3-2) but 0.8.5-3ubuntu1 is to be installed
```

Is going to be nearly impossible to get rid completely of ia32-libs because a lot of 3rd party programs depend on it, so while Ubuntu should try to remove it, they need to let people install it correctly if they need it.

---

### Post by vhaarr on 2011-08-26
Just downgrade libv4l again from the old packages found in /var/cache/apt/archives with dpkg -i.

Then everything works fine :)

---

### Post by jucas_lo on 2011-08-26
Sadly I have only version 0_0.8.5-3ubuntu1 on /var/cache/apt/ and not the previous version

---

### Post by shaneo1 on 2011-08-26
I have the same issue, but now I can not reinstall Wine1.2 or Wine1.3:

```
$ sudo apt-get install wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.2 : Depends: ia32-libs (>= 1.6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by jucas_lo on 2011-08-26
I found that basically the fix of [**808064**]("https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064") bug, breaks ia32-libs.

From the Bug:

```
v4l-utils (0.8.5-3ubuntu1) oneiric; urgency=low

  * Stop building the lib32* packages on amd64. LP: #808064.
  * Package requires symbols jpeg_mem_src and jpeg_mem_dest from jpeg8.
    Build-depend on libjpeg8-dev.
 -- Matthias Klose <email address hidden> Thu, 25 Aug 2011 18:30:26 +0200
```

So we can't install ia32-libs because there is no lib32v4l-0, because they don't build it anymore, since it is already multiarch, I think the solution would be to simply drop the dependency of ia32-libs on lib32v4l-0

---

### Post by shaneo1 on 2011-08-26
so how can we do that, im new to ubuntu :(

---

### Post by jucas_lo on 2011-08-26
We can't do anything for now, but the maintainers already know what they have to do and this problem affects quite a lot of people and packages, so I expect this would be fixed before the next beta

Or at least that's what I hope ;-)

---

### Post by shaneo1 on 2011-08-26
Do you know what the thread is on launchpad.  I would like to follow its progress.

---

### Post by jucas_lo on 2011-08-26
Hi for now this bug [https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064](https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064) against v4l-utils is listed as affecting ia32-libs & wine and is marked as high importance, so I think we should check that Bug for a fix

---

### Post by ratcheer on 2011-08-26
On my system, the proposed resolution (by aptitude) involves removing googleearth-stable. That sucks, too. :(

Tim

---

### Post by sumski on 2011-08-26
why don't you just replace lib32v4l with v4l:i386 in debian/control?

---

### Post by shaneo1 on 2011-08-26
> **sumski said:**
> why don't you just replace lib32v4l with v4l:i386 in debian/control?

How can I do that, please?

---

### Post by geojorg on 2011-08-26
Skype has the same problem. Can't install it.

---

### Post by cariboo on 2011-08-26
There has been a fix released, so you'll have to wait for the new ia32libs to propagate through the mirrors.

---

### Post by cgarre on 2011-08-26
i get this 

 sudo apt-get install ia32-libs 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ia32-libs : Depends: lib32v4l-0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I am unable to install directly too .. i am basically unable to install skype on ubuntu 11.10 .. not sure if i would have previously ... just wanted to install today .. my bad luck.

---

### Post by buzzmandt on 2011-08-26
wait a little while longer, mines installing now

---

### Post by shaneo1 on 2011-08-26
I've just added the wine repos [I]

ppa:ubuntu-wine/ppa

and 

Sudo apt-get install wine1.2 

Now the ia32-libs are downloading and installing,  I am sure this will also now work for Skype and the Android SDK.

:D  Good work guys :KS
[/I]

---

### Post by drodiger on 2011-08-27
It removed googleearth ia32-crossover-pro picasa skype wine1.3 acroread.

So most of the used 3rd party tools. By the way, I think acroread is not available anymore in partners section, is it?

---

### Post by drodiger on 2011-08-27
According to bug report [https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064](https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064) this has been fixed and I can install wine1.3 and picasa. (without adding any ppa)

Googleearth and skype don't have installation candidate.

---

### Post by cariboo on 2011-08-27
> **drodiger said:**
> According to bug report [https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064](https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064) this has been fixed and I can install wine1.3 and picasa. (without adding any ppa)

Googleearth and skype don't have installation candidate.

There is no partner repository for Oneiric yet, you can use the packages from the Natty repository

---

### Post by ratcheer on 2011-08-27
Everything updated on my system, this morning (i.e., no held updates, no conflicts). Google Earth is working just fine.

Tim

---

### Post by bcollier on 2011-09-07
I apologize for cross posting, I posted this on the bug and haven't heard a reply in two days.  In short, I am running Natty, I did a basic dist-upgrade two days ago and it broke wine1.3, Skype, and Adobe Air.  I use Skype and wine everyday for work so these are must have applications.  



In reading the bug report, it looks like they are discussing this as a 11.10 bug and they fixed it in the 11.10 repositories, but as I'm not a developer I don't understand what I would need to do to get this fixed on Natty.  Please help?


I've also tried installing the versions of the libraries it is looking for below (0.8.3-2 rather than 0.8.5-3) but the Ubuntu Software Center says I can't install it because I already have a later version.

---------------------


Posted on [https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064](https://bugs.launchpad.net/ubuntu/oneiric/+source/ia32-libs/+bug/808064)



I have this exact bug (below) but I am  still running Natty and came across this issue after an upgrade.  Skype  and Wine1.3 no longer work.  Is there a separate bug for Natty, or how  should I fix this?  I checked out the link above, but I'm unclear on  what I should do to resolve the issue.
 $ sudo apt-get build-dep wine1.3
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have unmet dependencies:
 ia32-libs : Depends: lib32v4l-0 but it is not going to be installed
 lib32v4l-dev : Depends: libv4l-0 (= 0.8.3-2~ppa1) but 0.8.5-3u1~ppa1 is to be installed
                Depends: lib32v4l-0 (= 0.8.3-2~ppa1) but it is not going to be installed
                Depends: libv4l-dev (= 0.8.3-2~ppa1) but 0.8.5-3u1~ppa1 is to be installed
E: Build-dependencies for wine1.3 could not be satisfied.
$ cat /etc/issue
Ubuntu 11.04 \n \l
 $ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

---

### Post by cariboo on 2011-09-07
@bcollier, your problem is different from what has been discussed here. In Oneiric we now have what is called multiarch, which allows us to install 32-bit programs on 64-bit systems without having to jump through a lot of hoops.

---

