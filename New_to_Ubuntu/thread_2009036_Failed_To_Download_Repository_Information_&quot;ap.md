---
title: "Failed To Download Repository Information &quot;apt-cdrom&quot;"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by rbscairns on 2012-06-23
I am using Ubuntu 12.04 with Gnome Classic. To update, I go to Applications>System Tools>Administration>Update Manager and clickon [Check]. The check proceedure then commences.

After a while, I get the following error message "Failed to download repository information" with the following details:

> W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Mycomputer is an ASUS eee B202 without CD drive attached (although I do have an external one available).

I have already selected the best download server. It happens to be mirror.nus.edu.sg/ubuntu.

How can I solve this Update Manager problem?

---

### Post by wildmanne39 on 2012-06-23
Hi, click dash>updates>settings>under ubuntu software uncheck install from cd/dvd rom.
Thanks

---

### Post by nipunshakya on 2012-06-23
> **rbscairns said:**
> I am using Ubuntu 12.04 with Gnome Classic. To update, I go to Applications>System Tools>Administration>Update Manager and clickon [Check]. The check proceedure then commences.

After a while, I get the following error message "Failed to download repository information" with the following details:



Mycomputer is an ASUS eee B202 without CD drive attached (although I do have an external one available).

I have already selected the best download server. It happens to be mirror.nus.edu.sg/ubuntu.

How can I solve this Update Manager problem?

Hello. Please open your update manager, click the settings button, and under the 'Ubuntu Software' tab, uncheck the Cdrom with ubuntu 12.04 'Precise Pangolin' . Type your password when prompted and then run an update. U won't have a trouble then... 

Happy Linuxing

---

### Post by rbscairns on 2012-06-23
Thank you to both WinuxUser and Wildmanne39. Your replies solved my problem.

Next time you get to Cebu, I owe you both a beer.

---

### Post by wildmanne39 on 2012-06-23
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

