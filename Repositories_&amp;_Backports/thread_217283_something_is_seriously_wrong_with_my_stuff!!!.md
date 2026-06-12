---
title: "something is seriously wrong with my stuff!!!"
date: 2006-07-16
forum: Repositories &amp; Backports
---

### Post by yourearthlymaster on 2006-07-16
Every time I start synaptic package manager, I get this error: 

The following problems were found on your system
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

Can anyone suggest what to so to fix this.  
I am still using breezy by the way.  

thanx in advance.

---

### Post by aysiu on 2006-07-16
Do you have the Breezy Badger CD-ROM in your CD drive? If not, you should disable that repository: go to **Settings** > **Repositories** and uncheck the box next to the CD source. Then click **Reload**.

---

### Post by yourearthlymaster on 2006-07-16
That seems blatantly obvious now that you pointed it out to me, I'' ma genius.  
thanx for that.

---

