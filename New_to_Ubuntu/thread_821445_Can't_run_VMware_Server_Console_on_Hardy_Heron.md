---
title: "Can't run VMware Server Console on Hardy Heron"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by mchoo on 2008-06-07
Hi all....

I'm an absolute N00b to the world of Linux and a novice in VMware, so please be gentle. :-)

Anyway.... I've just installed a Hardy Heron on my PC, and installed VMware server 1.06. Everything went smoothly, except the Perl thing, which was neither compulsory, nor necessary for me (the vmware-install.pl reported successful installation at the end anyway). HOWEVER, when I tried to run the VMware Server Console, it would not come up at all! Does anyone know what's wrong? 

Thanks.

---

### Post by quelx on 2008-06-07
Run is from the terminal **vmware-server-console** and notice the errors about missing libraries.

The fix:
[http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

---

### Post by mchoo on 2008-06-07
> **quelx said:**
> Run is from the terminal **vmware-server-console** and notice the errors about missing libraries.

The fix:
[http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

You Da Man! Thanks so much!

---

### Post by mchoo on 2008-06-08
> **quelx said:**
> Run is from the terminal **vmware-server-console** and notice the errors about missing libraries.

The fix:
[http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

Hi... I successfully installed VMware on 1 PC, but came across another issue on another PC. The vmware-install fails when trying to generate SSL certificate. It says: "Unable to get the last modification timestamp of the destination file /etc/vmware/ssl/rui.key". 

The 2nd PC is fairly similar to the 1st one. Both are AMD64 x2, with the exception that the 2nd one is less powerful (3600 vs 5000, 2GB DDR2-667 vs 4GB DDR2-800), also the mobo is different (Gigabyte vs. Asus). But those differences, I'd imagine, should have no bearing on the VMware install, shouldn't they?

Cheers

---

