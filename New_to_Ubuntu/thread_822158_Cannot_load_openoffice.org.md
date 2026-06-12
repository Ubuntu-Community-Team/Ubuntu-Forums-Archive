---
title: "Cannot load openoffice.org"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Corvair on 2008-06-07
Hello every one,

I have upgraded to 8.04 64 bit.
This is the first time I see this in two years of using Ubuntu.
I cannot install openoffice.org. nor word by itself.
I have open office draw, impress and I can use power point presentation.




As far as I know all the repositories are there, but then, what do I really know ???

Can any one help?


This is what I get when I try to install openoffice:

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

openoffice.org:
 Depends: openoffice.org-base but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
  Depends: openoffice.org-core (=1:2.4.0-3ubuntu6) but 1:2.4.1~rc1-1ubuntu1 is to be installed
 Depends: openoffice.org-filter-binfilter but it is not going to be installed
 Depends: openoffice.org-officebean but it is not going to be installed
 Depends: openoffice.org-writer but it is not going to be installed

---

### Post by avtolle on 2008-06-08
Have you run the updates that appeared after you installed before trying to install openoffice.org? BTW, FYI, there is a bug with openoffice.org which is being worked on which may be a part of your problem.  What I did was to not install the meta package, but installed the pieces through Synaptics, which went well, and appear to have avoided the bug (something to do with Latex). HTH.

---

### Post by st33med on 2008-06-08
OOo is installed by default in Ubuntu.

---

### Post by Corvair on 2008-06-08
It should have been installed by default but it was not.
Since there seems to be a problem I will wait for further updates which should solve the problem.

Thanks for your help.

---

### Post by avtolle on 2008-06-08
> **st33med said:**
> OOo is installed by default in Ubuntu.
Yes, it is and has been in the past, except on the 8.04 ppc version, it wasn't from a fresh install as I recall, and as I had done an distribution upgrade on my other G4, and had run into the bug, I merely installed all the pieces of Open Office without the meta package, and have had no issues thereafter.

---

### Post by forger on 2008-06-08
post this:
```
apt-cache policy openoffice.org
apt-cache show openoffice.org
```

you could file the bug for this meta package at [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by Corvair on 2008-06-08
OK, I have filled the bug

---

