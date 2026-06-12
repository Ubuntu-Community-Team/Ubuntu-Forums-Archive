---
title: "[SOLVED] Unstalling Virtualbox"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by betes on 2008-05-13
Hi all-

 I installed virtualbox-ose via apt-get.  I set it up and made a guest machine (running mandriva) to test it out. 

 I then deleted the machine (in the virtualbox giu) and uninstalled virtualbox-ose (using apt-get --purge).  But it leaves the /.virtualbox folder in my home directory which still contains the .vdi of the mandriva machine I made.  The .vdi is almost 3 gigs, so I'd like to get rid of it.  

Can I just delete the ~/.virtualbox directory, or is there some better way of getting rid of these files?

---

### Post by Sinkingships7 on 2008-05-13
> **betes said:**
> Hi all-

 I installed virtualbox-ose via apt-get.  I set it up and made a guest machine (running mandriva) to test it out. 

 I then deleted the machine (in the virtualbox giu) and uninstalled virtualbox-ose (using apt-get --purge).  But it leaves the /.virtualbox folder in my home directory which still contains the .vdi of the mandriva machine I made.  The .vdi is almost 3 gigs, so I'd like to get rid of it.  

Can I just delete the ~/.virtualbox directory, or is there some better way of getting rid of these files?


Just delete the directory.

---

### Post by Inxsible on 2008-05-13
Yup ....since you already have removed the app, you can just delete the .virtualbox folder.

---

