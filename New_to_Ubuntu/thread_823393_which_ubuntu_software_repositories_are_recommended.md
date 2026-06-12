---
title: "which ubuntu software repositories are recommended to be activated and what do you us"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by guest_user on 2008-06-09
which ubuntu software repositories are recommended to be activated and what do you use?

how safe is activating the multiverse and universe repos, as i am aware that security and bug fixes are not a guarantee for these repos?

---

### Post by kpkeerthi on 2008-06-09
Universe and multiverse give you the "restricted" stuffs like mp3 support and other propriertory softwares and drivers. 

In addition to the default already selected in System -> Admin -> Software Sources, I have backports and medibuntu enabled. 

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by hyper_ch on 2008-06-09
I have all the official ones, plus medibuntu, plus budgetdedicated for wine

---

### Post by SunnyRabbiera on 2008-06-09
most of the repositories you will see are trusted, medibuntu and the wine repositories are very reliable as is the multiverse and universe repo's

---

### Post by guest_user on 2008-06-09
so do u guys enable the multiverse and universe repos?

---

### Post by SunnyRabbiera on 2008-06-09
> **guest_user said:**
> so do u guys enable the multiverse and universe repos?

well I did, have no worries they will do you no harm.
I know its hard to trust things coming from a OS like windows but most of us are here to help...

---

### Post by shae on 2008-06-09
I personally use main, restricted, universe, multiverse, and backports all the time.  I also use the security and updates repository.  I consider these safe.

I sometimes enable proposed for a particular update and then comment them out.

I also use medibuntu's repo for codecs and skype.

I use Dell's PPA and my personal PPA for Wine for Warcraft 3.

---

### Post by guest_user on 2008-06-10
when i try to enable winehq repository, i get this error message when i reload the package lists:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found [IP: 88.159.206.7 80]
Some index files failed to download, they have been ignored, or old ones used instead.

how do i solve this?

---

### Post by SunnyRabbiera on 2008-06-10
the wine server sometimes goes wonky, I have noted this behavior.

---

### Post by guest_user on 2008-06-10
so the solution = i just wait for it to go not so wonky right?

---

