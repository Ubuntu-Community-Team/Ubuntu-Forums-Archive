---
title: "[SOLVED] How to delete programs/software???"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-05
Ubunteros,

I'd like to learn the RIGHT way to remove software programs I've installed.

I know that anything installed via Synaptic can be easily uninstalled using Synaptic BUT how about programs that are installed through a download from a web site?

I'm not to sure how to go about this.

Any ideas?

---

### Post by beno1990 on 2008-11-05
When you say "programs downloaded from a website", I take it you mean .deb packages?

---

### Post by Coreigh on 2008-11-05
If they are .deb packages then dpkg is the tool to use.
man dpkg

However if you are referring to custom built, binary or third party applications then you basically need to know what they did when they installed. If they left an install log that is great, track everything down and delete it. If they modified other files you may need to re-install them or re-configure with dpkg.

Does anyone more experienced have advice?

---

### Post by handydan918 on 2008-11-05
> **suomalainen said:**
> Ubunteros,

I'd like to learn the RIGHT way to remove software programs I've installed.

I know that anything installed via Synaptic can be easily uninstalled using Synaptic BUT how about programs that are installed through a download from a web site?

I'm not to sure how to go about this.

Any ideas?

It depends on the means of installation.
If the package was a .deb file, then the package manager can remove it. If it was a  tar.gz or something, then you will have to locate the readme for the software and see what it specifies.  If it's a nice tidy program that installs in a single directory, the a simple rm -rdf <packagename> should suffice.

---

### Post by Paqman on 2008-11-05
Ease of removing software is another good reason to always stick to the package manager.

Synaptic, Add/remove or apt-get/aptitude can cleanly uninstall any package installed through the package manager (ie: Add/Remove, Synaptic, Update Manager, .debs, apt-get, aptitude)

Installing things besides .debs or from the repos gets messy at uninstall time, and is best avoided. As mentioned, some apps are provided with an uninstall script that can minimise the grief, but it's a bit of a lottery.

---

### Post by suomalainen on 2008-11-05
Thank you very much for the replies. Yes this was a .deb package I installed. I didn't realize until after it was pointed out that after install I could refer to the package manager to uninstall... Regardless, that's what I did and program is now removed.

---

