---
title: "Softwares are old!"
date: 2008-11-23
forum: Programming Talk
---

### Post by MagiSu on 2008-11-23
Eclipse, I bet every programmer knows this, has the version 3.2.1 in 8.10. We know we have 3.4 already! And for KDevelop, the 3.5.3-2 has already prepared while we only have 3.5.3-0. Can anybody in Canonical fix this? Thanks!

---

### Post by Zugzwang on 2008-11-23
Canonical has a deadline after which only bug-fixes of the current version at that date find their way into the distribution. If you want later versions, you need to wait until the next Ubuntu release or install the respective versions of your software manually.

EDIT: See [here]("https://wiki.ubuntu.com/JauntyReleaseSchedule") for the release schedule for the next version. As you can see, software versions that are not in Debian prior to Christmas will not make it into the next release in April. The reason for this policy is that last-minute changes in some packages can break certain functionalities and the Ubuntu team needs to time to fix this.

---

### Post by CptPicard on 2008-11-23
Uh, the KDevelop isn't old, looking at the version number.

Don't use the Eclipse from repos, it's easy enough to just download 3.4 and extract it under /opt. I do that to both Eclipse and Netbeans.

---

### Post by jespdj on 2008-11-23
This has already been reported in the bug tracking system for Eclipse: [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/123064](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/123064)

And for NetBeans: [https://bugs.launchpad.net/ubuntu/+source/netbeans-ide/+bug/251173](https://bugs.launchpad.net/ubuntu/+source/netbeans-ide/+bug/251173)

Note: If you find something like this, you can report it yourself in Launchpad.

---

### Post by snova on 2008-11-23
They didn't make it into the repos in time for the release is all. And Eclipse isn't the easiest thing to package, either.

For Eclipse, I suggest you just download and extract it somewhere in your home directory.

KDevelop is in the middle of a rewrite for KDE 4. The SVN version will build, so you might be interested in that. Unfortunately it depends on the trunk of kdelibs...

---

### Post by bobbocanfly on 2008-11-23
Eclipse is famously old in Ubuntu. Take it from an Ubuntu developer: It is a mission to package up. Java stuff is difficult to package and Eclipse being so complex doesnt help either. IIRC, a new version should be in Jaunty.

---

### Post by CptPicard on 2008-11-23
> **bobbocanfly said:**
> It is a mission to package up.

Yet, a tgz from eclipse.org is fine enough a package, and installation is a one-liner.. :)

---

### Post by bobbocanfly on 2008-11-23
> **CptPicard said:**
> Yet, a tgz from eclipse.org is fine enough a package, and installation is a one-liner.. :)

Hehe. True, but then you miss out on the advantages of a package manager. Unfortunately Debian packaging is amazingly complex (a lot more than it really needs to be tbh). It will be brought in when Debian get their act together, then we merge the Debian version with our current changes; so if you want something done quickly, go hassle the Debian guys :P

---

### Post by CptPicard on 2008-11-23
> **bobbocanfly said:**
> True, but then you miss out on the advantages of a package manager.

Sure, but in this case you don't even really need the package manager for anything... not much depends on Eclipse outside of Eclipse plugins/"products", and the only real dependency of Eclipse is the JDK...

---

### Post by snova on 2008-11-23
I wouldn't know, but I'd guess the difficulty is partially in getting the plugins packaged correctly. Eclipse is split into many packages, which are essentially sets of plugins that depend on the base platform.

---

### Post by CptPicard on 2008-11-23
Just use Eclipse's built in software installation/update system. Works great.

---

### Post by bobbocanfly on 2008-11-23
Yeah, part of the difficult comes from the huge amount of stuff that needs to be included. For example the main "eclipse" source package builds 16 different binary packages (the most I have ever seen in a year of packaging for Ubuntu). Also part of the difficult came/comes from the fact we have only just decided on which versions of Java to have in main, and trying to get eclipse to work with them all.

---

### Post by jespdj on 2008-11-24
> **bobbocanfly said:**
> Also part of the difficult came/comes from the fact we have only just decided on which versions of Java to have in main, and trying to get eclipse to work with them all.
Eclipse works fine with OpenJDK Java 6 and Sun Java 6 - there's nothing special that you have to do to get it to work.

---

