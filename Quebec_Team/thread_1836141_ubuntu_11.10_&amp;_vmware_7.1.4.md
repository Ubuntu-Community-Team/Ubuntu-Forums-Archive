---
title: "ubuntu 11.10 &amp; vmware 7.1.4"
date: 2011-08-30
forum: Quebec Team
---

### Post by dratte490 on 2011-08-30
bonjour, j'ai installer ubuntu 11.10 et ensuite fais les upgrade, j'ai installer vmware-workstation-full 7.1.4, sa a bien passer, mais quand je lance l'application, j'ai un message d'erreur: kernel module updater,vmware must be compiled & load into the kernel
je fais install mais il plante plus loin disant, yé pas capable.
que puis-je faire?
merci

---

### Post by andrea.annoe on 2011-10-16
Hi,
do you try to upgrade to Vmware Workstation 7.1.5

...I try now.

From log I think that problem is program GCC in linx 11.10, version 4.6 

With this version Vmware Workstation isn't able to compile module for kernel linux 3.0

Stay tune.
Andrea.

---

### Post by andrea.annoe on 2011-10-16
Hi,
try to read this post, very interesting: 



After spending some time browsing for help, I found

[http://weltall.heliohost.org/wordpress/2011/05/14/running-vmware-workstation-player-on-linux-2-6-39-updated/](http://weltall.heliohost.org/wordpress/2011/05/14/running-vmware-workstation-player-on-linux-2-6-39-updated/)

Weltall's blog mentions that the patches made available at the above location work also for

linux 3.0.0-rc1.

 

I downloaded and applied them to my linux 3.0.0-1-686-pae system and there they work fine

too. The modules load and install fine, so the problem has been solved.

 

The patch is at [http://weltall.heliohost.org/wordpress/wp-content/uploads/2011/05/vmware2.6.39patchv3.tar.bz2](http://weltall.heliohost.org/wordpress/wp-content/uploads/2011/05/vmware2.6.39patchv3.tar.bz2)

and even though it says 2.6.39 it works fine for 3.0.0 as well, AFAICS.

 

After downloading and extracting the archive you get two files: vmware2.6.39fixedv3.patch and

patch-modules_2.6.39.sh. Simply run ./patch-modules_2.6.39.sh to apply the patches and install the modules.

---

