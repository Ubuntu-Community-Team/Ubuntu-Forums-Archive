---
title: "problem with update manager"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ayirusp on 2011-10-07
hi there!:o

I've got a problem with update manager while trying to update my ubuntu 11.10. The update manager failed to work and it came up with the following:

"Run a partial upgrade, to install as many updates as possible.
 This can be caused by:
   A previous upgrade which didn't complete
  Problems with some of the installed software
  Unofficial software packages not provided by Ubuntu
  Normal changes of a pre-release version of Ubuntu"


However, I've tried to ran some commands as described below;


sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Yet, the problem has not been solved. What should I do to handle with this problem. Anyone can help me? 

Thank you so much

ayirusp

---

### Post by collisionystm on 2011-10-07
> Normal changes of a pre-release version of Ubuntu

Download a daily image. Upgrading takes like 2 hours.

Download an image, backup your stuff to another drive and install fresh.

---

### Post by cariboo on 2011-10-07
> **ayirusp said:**
> hi there!:o

I've got a problem with update manager while trying to update my ubuntu 11.10. The update manager failed to work and it came up with the following:

"Run a partial upgrade, to install as many updates as possible.
 This can be caused by:
   A previous upgrade which didn't complete
  Problems with some of the installed software
  Unofficial software packages not provided by Ubuntu
  Normal changes of a pre-release version of Ubuntu"


However, I've tried to ran some commands as described below;


sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Yet, the problem has not been solved. What should I do to handle with this problem. Anyone can help me? 

Thank you so much

ayirusp

If update manager offers a partial upgrade, it's better to go away for a while, and try later. If you are already running Oneiric, try synaptic instead, as it will tell you what it's going to do.

---

### Post by sammiev on 2011-10-07
> **cariboo907 said:**
> If update manager offers a partial upgrade, it's better to go away for a while, and try later. If you are already running Oneiric, try synaptic instead, as it will tell you what it's going to do.

+1 for synaptic as it will give you a warning. Partial upgrades can give you problems.

---

### Post by grahammechanical on 2011-10-07
When I get that message I just click Close and then click Install Updates to download the 11.10 updates that are waiting. I have been doing this every night since alpha 2.

For the last couple of days I have been getting a Failed to download repository information - check your internet connection message when I click Check. I have also been getting a red warning icon when update manager searches for any updates of its own accord.

I can still do updates and my internet connection is working so

I wonder are the development release repositories locked off in the days before the development release turns into a distribution release so that the package maintainers can get to work on the repositories?

Regards.

---

### Post by cariboo on 2011-10-07
There is no human intervention between the time a package is submitted to the build farm and when it shows up in the repositories. You are more than likely running into the same thing I've run into where packages aren't available for download, because they are in the process of being updated, retrying the download a couple of minutes later works properly.

---

