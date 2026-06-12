---
title: "Question about deb packages"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by LinuxFox on 2008-11-18
I was browsing GetDeb and I notice they have packages for Intrepid, I want to know if these packages were installed on a machine with Hardy, would they cause any problems?

I thought deb packages are the same in general.  Does one have requirements and features that the other doesn't?

Just thought I'd ask in case I download a deb package online.  Not just from GetDeb, but from maybe elsewhere (like an official site to the said software).

---

### Post by mikewhatever on 2008-11-18
Newer packages may have newer dependencies, which, in turn, may or may not cause problems. Certain dependencies will not be available with older versions, for example.

---

### Post by tjwoosta on 2008-11-18
why would you want to install intrepid packages in hardy?

getdeb.net has both intrepid and hardy packages availible

---

### Post by LinuxFox on 2008-11-18
tjwoosta, thanks but I'm aware they have Hardy packages.  I just asked because I thought all deb packages were universal.  For example, if I went to a website for the software (like a site run for the developers), they might have the latest version in a deb package.  If they didn't specify an Ubuntu version, I could end up downloading the package for the wrong version of Ubuntu without realizing it.  That's why I ask.

mikewhatever, dependencies could be a good reason as well.  Wouldn't the dependencies also install on other versions if they're also in deb packages?

---

### Post by mikewhatever on 2008-11-18
> **LinuxFox said:**
> 
mikewhatever, dependencies could be a good reason as well.  Wouldn't the dependencies also install on other versions if they're also in deb packages?

The thing is, dependencies are not in/inside the deb package you install, they are different other debs and usually get pulled in from the repositories.

---

### Post by LinuxFox on 2008-11-18
> **mikewhatever said:**
> The thing is, dependencies are not in/inside the deb package you install, they are different other debs and usually get pulled in from the repositories.Thanks, but I meant the dependencies themselves.  For example, SDL would have a deb package separate.

---

