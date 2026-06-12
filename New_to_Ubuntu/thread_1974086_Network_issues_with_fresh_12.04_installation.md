---
title: "Network issues with fresh 12.04 installation"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by Illoran on 2012-05-05
Hi,

i got stuck in some trouble with my wired network connection. I've installed Ubuntu 12.04 freshly to a brand new computer and Ubuntu insists on not detecting my onboard network controller. The Mainboard is an ASUS P8H77-V and via lspci i get the information that the ethernet controller works fine ( an Atheros AR8161 ) but the network controller won't be even listed. Everything works fine under the parallel operating windows system on the same machine so its obviously no hardware problem.

any ideas ?

Illo

---

### Post by Daveth on 2012-05-05
not looking good at the moment:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782)

---

### Post by Illoran on 2012-05-06
Thanks for the reply. That means no network support will be available shortly, and i have to wait to get it running until the kernel and/or driver is fixed ?

illo

---

### Post by Julien14 on 2012-06-26
> **Illoran said:**
> Thanks for the reply. That means no network support will be available shortly, and i have to wait to get it running until the kernel and/or driver is fixed ?

illo


Hello

Look at [http://www.jfdesignnet.com/?p=2133](http://www.jfdesignnet.com/?p=2133) : it worked for me.

You need to do it again if you update your kernel.

Take care for comment #6

---

