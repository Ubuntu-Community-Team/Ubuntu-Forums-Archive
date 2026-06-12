---
title: "IcedTea-Web Plugin 1.5.2-1ubuntu2"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by mdavis1231 on 2015-03-18
I've updated to OpenJDK-8 on my Ubuntu 14.04 LTS.  Does anyone know of a way to install IcedTea-Web Plugin 1.5.2-1ubuntu2 other than installing a .deb package?  Otherwise, I have to keep OpenJDK-7 on my OS and keep using IcedTea-Web Plugin 1.5-1ubuntu1 and use sudo update-alternatives --config java to choose OpenJDK-8 as my default.  I'd rather just be able to remove OpenJDK-7.

---

### Post by DuckHook on 2015-03-18
I've nuked both and refused to allow them on my system since 10.04, so am going by a combo of memory and educated extrapolation, but isn't icedtea already in the repos? To my understanding, all you need to do is:```
sudo apt-get purge openjdk-8-jre && sudo apt-get install icedtea-plugin
```...that is, if you installed openjdk from the repos. If not, then it all depends on how you installed it.

---

### Post by mdavis1231 on 2015-03-19
I actually installed OpenJDK-8 from ppa, because it's not in the repos for Ubuntu Trusty Tahr 14.04 LTS.  And if I uninstall OpenJDK-7, it installs OpenJDK-6.  Then if I try to uninstall that, it wants to uninstall a whole bunch of other stuff that I need.  It seems that IcePlugin 1.5.2-1ubuntu2 is available in Ubuntu 14.10 Utopic Unicorn & Ubuntu 15.04 Vivid Velvet, but not in Trusty.

---

### Post by DuckHook on 2015-03-20
> **mdavis1231 said:**
> I actually installed OpenJDK-8 from ppa, because it's not in the repos for Ubuntu Trusty Tahr 10.04 LTS.  And if I uninstall OpenJDK-7, it installs OpenJDK-6.  Then if I try to uninstall that, it wants to uninstall a whole bunch of other stuff that I need.Likely because you subsequently installed a whole bunch of apps which depend on some form of Java. Put another way, the system is smart enough to extrapolate that if you want to nuke a key app like Java, then any other app which will break without the presence of Java must also go. You may have to uninstall all that stuff in order to start over with a pristine environment. Here is a good moment to remind you to back up absolutely everything of value to you before proceeding further, in case you break dpkg and end up having to reinstall the system. I'm on shaky ground advising you with PPAs because, by using one, you've messed with DPKG's database. However, it seems to me that the old *sudo apt-get purge name_of_pkg* routine should suffice. You will likely have to purge both the pkg installed through the PPA *and* the pkg installed from the repo. *Make sure* the PPA is attached and active in your software sources before you purge, then make just as sure the PPA is deleted after purge is successful, but only if purge is successful.> It seems that IcePlugin 1.5.2-1ubuntu2 is available in Ubuntu 14.10 Utopic Unicorn & Ubuntu 15.04 Vivid Velvet, but not in Trusty.Do you have backports turned on? Even if turned on, it is more likely than not that the developers do not have a 14.10 version of icedtea approved yet for 14.04. There may be stability problems, or they just can't guarantee trouble-free performance to their satisfaction. If so, then do you really want to go for it? Is the payoff really worth the potential destabilization of your entire production system? Only you can decide.

I ask this because people who use LTS releases are usually after system stability more than anything else. If you want a pkg built for 14.10, you may be better off just upgrading to 14.10, where the pkg has been tested to work with the OS version.

---

### Post by mdavis1231 on 2015-03-20
I do have backports enabled for my 14.04 LTS.  I did manage to uninstall OpenJDK-7 last night which installed OpenJDK-6, which I then uninstalled.  However, when I tried to reinstall only IcedTea-Web Plugin 1.5-1ubuntu1, it insisted that I also install OpenJDK-7.  I guess until (or if) they approve IcePlugin 1.5.2-1ubuntu2 for 14.04for 14.04 for 14.04 backports, I'll have to keep both OpenJDK-7 and OpenJDK-8 installed, and simply configure OpenJDK-8 as default.

Has anyone heard of or have any idea if they're working on IcePlugin 1.5.2-1ubuntu2 for 14.04 LTS backports?

---

