---
title: "what does this mean"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by blake7 on 2008-08-18
E: /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb: subprocess pre-installation script returned error exit status 1


dthank you for your time

---

### Post by Dill on 2008-08-18
What command did you enter to yield that output?

---

### Post by Majorix on 2008-08-18
If you were trying to install Sun's JRE it might be that you rejected the end-user agreeement.

---

### Post by rockerphil on 2008-08-18
> **Majorix said:**
> If you were trying to install Sun's JRE it might be that you rejected the end-user agreeement.

this would be my guess, cus /var/cache/apt/archives is where .deb packages are downloaded to when installing via apt-get, aptitude, Add/Remove or Synaptic, and it says somthing about a pre-install error. so i'd try to reinstall and make sure you accept the EULA

---

### Post by blake7 on 2008-08-19
thank  you everone

---

