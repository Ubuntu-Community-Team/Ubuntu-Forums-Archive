---
title: "problem related with ubuntu repositories"
date: 2009-01-14
forum: Repositories &amp; Backports
---

### Post by dsharmaa on 2009-01-14
Hi, 

I am trying to use these two steps but I think there is some problem with ubuntu repositories. Can anybody please help me?

      sudo apt-get build-dep linux-image-2.6.22-14-generic linux-ubuntu-
modules-2.6.22-14-generic
      apt-get source linux-image-2.6.22-14-generic linux-ubuntu-
modules-2.6.22-14-generic

thanks in advance, 

Cheers
DP

---

### Post by dsharmaa on 2009-01-14
Hi, 

Sorry I forget to give more information. I am using ubuntu7.10 and I am getting following messages 

root@ubuntu-desktop:/usr/src# apt-get source linux-image-2.6.22-14-generic linux-ubuntu-modules-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for linux-source-2.6.22
 
thanks, 

Cheers,
DP

---

