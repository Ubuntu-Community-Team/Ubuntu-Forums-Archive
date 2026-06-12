---
title: "Relatable source for software packages."
date: 2022-10-23
forum: New to Ubuntu
---

### Post by sash5 on 2022-10-23
I’m new to Ubuntu and looking for a secure way to get software packages. There are 4 standard repositories in Ubuntu but a lot of packages are old, and if I add some  third party repositories than I have to trust the publisher. But there is no statistics and reviews in one place. An example of a good place for software packages is chocolatey, there you can see statistics, reviews and a lot of other information, but it’s windows only. If there such a repository for Linux?

---

### Post by grahammechanical on 2022-10-23
Statistics and Reviews do not equal secure software. There are only a measure of popularity. A statistic for the number of downloads should not be taken as a measure of the number of users of that software. A person may download an application and then remove it because of it not meeting their needs.

If we are using a Ubuntu LTS (Long Term Support) version then certain main applications will be upgraded during the support period of that release. Newer versions of other software appear in the Ubuntu Software store in the latest releases of Ubuntu. Provided the developers of the application have upgraded the software.

If our focus is on trusted sources of software then choose applications from the Ubuntu Software application. We may need to learn something about the differences between the Ubuntu software repositories and the security measures that are applied when software is packaged as a Snap or Flatpak or Appimage.

Regards

---

### Post by ajgreeny on 2022-10-23
There are also PPA repositories but some of those are no less risky than just searching online for a package for Ubuntu.
I use a few of those on my systems but only ones which I've been using for a long time and have grown to trust. My chromium browser comes from a PPA as does my Libreoffice, chromium because I do not use snap packages, and Libreoffice simply to get a 7.4 version in place of 7.3.
Both have been working very well but could be different for other users.

Before enabling a PPA its worth asking here for other user's thoughts about their safety.

---

### Post by Impavidus on 2022-10-23
How old is too old? The versions of software in each Ubuntu release get frozen shortly before release. Bugfixes get backported (at least for the main repository), but you don't get the new features. That makes it slightly older, but also more reliable and secure. If you go from one LTS release to the next, your software will be 2.5 years behind when the upgrade to the next LTS release is offered. Is that too old? Most think not, but I sometimes think it is. I use the interim releases, so my software is never more than one year behind. I plan to fresh install 22.10 soon, wiping my old 18.04 system and keeping my current 22.04 as a backup.

Some software gets updated inbetween, like thunderbird. Or you could use a PPA, but you've to use your own judgement to decide whether you consider it secure enough. For some big projects like libreoffice, the project maintainers themselves keep a PPA, which is considered reliable. Or you could use an alternative packaging method, like snap, which has additional security features, at some usability cost. Firefox comes that way by default these days, so it can no longer be used to read html documentation on my own system. I think it's time for me to fix that.

---

### Post by sash5 on 2022-10-23
> **grahammechanical said:**
> Statistics and Reviews do not equal secure software. There are only a measure of popularity.
But the probability that security problems in software that was downloaded 10k times and review 100 times detected are higher then if it was only 10.


> **grahammechanical said:**
> 
Ubuntu Software  store

Is the Ubuntu Software  store not the same as Snap?

Do i understand it correct if you install software from Snap or Flatpak you should trust the publisher?
So before you install you should do a research, for example using google.

What is the proper way, or algorithm to install the software and be more or less sure that you don't install some malware or a software with a lot of security holes?

---

### Post by grahammechanical on 2022-10-24
> Is the Ubuntu Software  store not the same as Snap?

No, it is not. Snap is a software package format. Ubuntu is based upon Debian and most of the software in Ubuntu is packaged in the Debian package format called deb. Snap is a newer concept of software packaging developed by Ubuntu developers. What are the differences? A deb package application will have access to all folders in the operating system. A snap packaged application is severely confined and has limited access to folders in the operating system.

Ubuntu Software was designed to install and remove deb packaged applications. A separate Snap Store was provided to install and remove snap packaged applications. Things have moved on. The latest versions of Ubuntu have a version of Ubuntu Software that is itself a snap packaged application and should be able to install and remove both deb and snap packaged applications.

Ubuntu developers do a few things to make sure that the software we install can be trusted. Applications (deb) installed through Ubuntu Software are code audited to confirm that they do not contain malicious code. Ubuntu also has a utility call AppArmor. Applications are associated with profiles and AppArmor makes sure the application does not move outside its profile.

> AppArmor is a Mandatory Access Control (MAC) system which is a kernel  (LSM) enhancement to confine programs to a limited set of resources.  AppArmor's security model is to bind access control attributes to  programs rather than to users.

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

Snap packaging uses a different approach. An application developer has to declare everything the application is designed to do in a file called a manifest. Then the snap packaging process uses the manifest to confine the application to the processes defined in the manifest as well as the built in confining of the application from accessing and changing system files.

[https://ubuntu.com/core/services/guide/snaps-intro](https://ubuntu.com/core/services/guide/snaps-intro)

I have little understanding of the security measures that Flatpak and AppImage put in place.

Regards

---

### Post by sash5 on 2022-10-24
> **grahammechanical said:**
> 

Snap packaging uses a different approach. An application developer has to declare everything the application is designed to do in a file called a manifest. Then the snap packaging process uses the manifest to confine the application to the processes defined in the manifest as well as the built in confining of the application from accessing and changing system files.

[https://ubuntu.com/core/services/guide/snaps-intro](https://ubuntu.com/core/services/guide/snaps-intro)


That means that only developer of the snap package is responsible for security of that packages, and you have to trust the developer, community in not involved. Is it right?

---

