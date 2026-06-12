---
title: "[SOLVED] why does installation always need the internet"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by koba101 on 2008-09-11
Hi,

This is mainly  a technical question, but why is it everytime i need to install something or remove and install something again.  Files get downloaded from the internet

aren't these files already available when i install ubuntu?

for example 

sudo apt-get install startupmanager

why would this download files?

---

### Post by oilchangeguy on 2008-09-11
> **koba101 said:**
> Hi,

This is mainly  a technical question, but why is it everytime i need to install something or remove and install something again.  Files get downloaded from the internet

aren't these files already available when i install ubuntu?

for example 

sudo apt-get install startupmanager

why would this download files?

don't know about the start up manager. but no, every file can't fit on one cd. and there's no reason to do manual updates. ubuntu will tell you when updates are available.

---

### Post by bobnutfield on 2008-09-11
startupmanager, and other apps, are help in the repositories which are accessed via the internet.  They are not held in a database on your computer.  If you tried to install without an internet connect, it could not retrieve the package and would fail.  You can, however, install some of the packages on the Ubuntu install CD that were not installed during your initial install.  But, it the package isn't on the CD, you will have to retreive it from the repos via the net.

---

### Post by oldos2er on 2008-09-11
> **koba101 said:**
> Hi,

This is mainly  a technical question, but why is it everytime i need to install something or remove and install something again.  Files get downloaded from the internet

aren't these files already available when i install ubuntu?

for example 

sudo apt-get install startupmanager

why would this download files?

 I'm not sure I understand your question; but "install" in this context means downloading program files from Ubuntu's repositories, which are internet-accessible servers. It's simply not possible to have every program you might ever want or need "already available" when you install Ubuntu.

---

### Post by cariboo on 2008-09-11
THere are far more programs available than there is room on the LiveCD. The CD just has enough to run Ubuntu on the cd, any extras need to be downloaded and installed. The last I heard there are over 20,000 packages in the repositories, not all of them are programs, there are a lot of supporting libraries.

Another reason that you need to download programs is that Ubuntu is not a static distribution, unlike other operating systems, there are always security updates  and bug fixes, so that the program you install today may be different a different version a couple of weeks from now.

Jim

---

### Post by koba101 on 2008-09-12
thanks for the replies, i got it now

---

