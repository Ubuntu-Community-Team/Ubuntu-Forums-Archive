---
title: "Updating the OS"
date: 2016-03-02
forum: New to Ubuntu
---

### Post by hmiersch on 2016-03-02
Hi.
the other day I found out that I can update to 15.10 using the software updater. So here are some questions.
- if I do that, will my installed software and config still be there?
- should I update? What has changed between 14.04 and 15.10? Should I wait for 16.04?
- are there any known issues with 15.10?
- if I use the software updater, will that sort my swap space issue? When I boot 14.04, I get an error telling me the swap drive is not ready yet. Some kind of bug with cryptswap, IIRC. Has that been fixed?

---

### Post by westie457 on 2016-03-02
Unless you have an urgent need to upgrade I say wait for 16.04.
The upgrade to 15.10 might cause some breakage especially if you have to upgrade to 15.04 first. 

No idea about the 'swap' issue as I do not use cryptswap.

---

### Post by ian-weisser on 2016-03-02
> **hmiersch said:**
> - if I do that, will my installed software and config still be there?
Perhaps. It depends upon what you installed, and what sources you installed from.
Applications that are in both 14.04 and 15.10 and that you installed from the Ubuntu repositories should uptade easily.
Applications that are not in 16.04 won;t update, and may become unusable.
Applications that you installed from non-Ubuntu sources (PPAs, third-party repos) may break the upgrade. Uninstall them before upgrading. The non-Ubuntu versions may not work after upgrading.

> **hmiersch said:**
> - if I use the software updater, will that sort my swap space issue? 
Perhaps. It depends upon the underlying reason for your swap issue.
Upgrades solve some problems, and don't solve others.

---

### Post by coldraven on 2016-03-03
I say wait for 16.04 then backup all your data and do a clean install. I never do upgrades because they have caused me problems in the past.

---

