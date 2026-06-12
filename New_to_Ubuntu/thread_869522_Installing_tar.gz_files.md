---
title: "Installing tar.gz files"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by pkj on 2008-07-24
Hi,
Have downloaded openoffice 2.4
Its a tar.gz file

How do i install it ????

pkj

---

### Post by Bucky Ball on 2008-07-24
[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

That should give you some ideas. Good luck ...

---

### Post by iaculallad on 2008-07-24
> **pkj said:**
> Hi,
Have downloaded openoffice 2.4
Its a tar.gz file

How do i install it ????

pkj

Here, follow this [link]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68") which will open you to OpenOffice Community Forum's solution on installing from tarball.

---

### Post by Bucky Ball on 2008-07-24
Incidentally, if you go Applications->Add/Remove and do a search for Openoffice, you will achieve an install much more easily. But a good idea to know how to untar anyhow ...

Unless you have a particular reason to manually install, try applications->add/remove or synaptic package manager search first perhaps when looking for software.

---

### Post by pkj on 2008-07-26
using tar -vxzf i have been able to untar the Openoffice 2.4 tarball..

Following files are now available
installdata  JavaSetup.jar  licenses  readmes  RPMS  setup  update

How do i go further with the upgradation of Open office 2.4

pkj

---

### Post by hyper_ch on 2008-07-26
why don't you install OOo from the repos?

---

### Post by Paqman on 2008-07-26
You can get a [.deb of Open Office 2.4.1](http://download.openoffice.org/other.html#en-US) from their website.

You should avoid installing packages from tarballs if at all possible. It messes up the dependency system in the package manager, which can lead to an unstable system.

The 2.4 version is available in the repos, which is always the first place you should go to get software.

---

### Post by pkj on 2008-07-26
How do i install it from repos...

Syneptic packet manager does not find openoffice 2.4

pkj

---

### Post by eightmillion on 2008-07-26
If you're running Ubuntu Hardy, the package in the repos is 2.4. Open up a terminal and type "sudo aptitude install openoffice.org-base". Then enter your password and it should install.

---

### Post by nvteighen on 2008-07-26
1. Reload the packages information.

2. Search "openoffice.org" (EDIT: or "openoffice.org-base" for a compact install). It will install the latest version available (2.4.1, by the way).

3. If it doesn't work, what Ubuntu version are you running?

---

### Post by pkj on 2008-07-26
I am on Fiesty

Openoffice.org is found by Syneptic.. However its re-installation does not migrate openoffice to 2.4

pkj

---

### Post by hyper_ch on 2008-07-26
then update to hardy

---

### Post by sharks on 2008-07-26
better install from synaptic.

---

### Post by pkj on 2008-07-26
i would like to install from synaptic, but how do i do that..
Do i remove the openoffice 2.2 first...or how do i go about it..

pkj

---

### Post by pkj on 2008-07-26
My syneptic shows version 2.2 even after i have included latest patches from the net
pkj

---

### Post by nvteighen on 2008-07-26
> **pkj said:**
> My syneptic shows version 2.2 even after i have included latest patches from the net
pkj
That's because you're on an old Ubuntu (two versions behind!).

Ubuntu has improved a lot since Feisty. Go here to get the newest Live CD [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) (Hardy Heron 8.04). **BACKUP YOUR DATA** and install. The last Ubuntu comes with OpenOffice.org 2.4 installed by default.

If you managed to install Feisty, then just repeat the steps to install Hardy. Probably things will work even better.

If you know how to do it, you can also do a dist-upgrade so you don't have to download the CD image... But that will require two upgrades (Feisty->Gutsy; Gutsy->Hardy) and it may fail.

Yes... it's a bit pain to tell you to upgrade the whole system to just upgrade OpenOffice... but it may even be easier than installing a .tar.gz and resolving dependencies.

---

### Post by Paqman on 2008-07-28
You *might* be able to install OO.o 2.4 on Feisty using the .deb available on their website.

The most likely problem you will encounter is that it might depend on some other file which isn't a high enough version in Feisty repos.

---

### Post by DarinB on 2008-07-28
my experience for 3 versions better not upgrade stick with what ever you have.
when you finally go to gutsy then hardy you will get the latest version.
oo 3.0 is out on beta and will be in the intrepid repos as a beta it is really good. And worth tho wait for the final version.

---

### Post by Bucky Ball on 2008-07-29
> Ubuntu has improved a lot since Feisty.

Indeedy. My advice, don't upgrade through the versions (or synaptic-takes hours), wipe and install Hardy. Good luck.

---

