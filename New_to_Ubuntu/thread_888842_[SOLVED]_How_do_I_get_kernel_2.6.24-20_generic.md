---
title: "[SOLVED] How do I get kernel 2.6.24-20 generic"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-08-13
Right now my system is running off of 2.6.24-19 generic and I wanted to update it to 2.46.24-20 generic, so it would be using the most up to date kernel.  I never received a message through update manager to load the new kernel.  How would I go about doing it manually.  Please try to keep your answers as easy as possible since I am no wiz at doing this type stuff.  Would there be a website somewhere showing step by step how to do this?

---

### Post by Flyingjester on 2008-08-13
it is complicated to compile your own kernel, kernel updates through distributions are usually modified kernels from the developers, if you are really interested in doing it, i suggest you take a look at [http://kernel.org/](http://kernel.org/) and [http://linuxplanet.com/linuxplanet/tutorials/202/1/](http://linuxplanet.com/linuxplanet/tutorials/202/1/)

---

### Post by WRDN on 2008-08-13
As far as I know, 2.6.24-20 is the kernel used in Intrepid Ibex, and will be released with that. If you want to upgrade to Intrepid Ibex now (though this is not advised on production machines), you can type "sudo update-manager -d" in the terminal.

---

### Post by Ryadt on 2008-08-13
Enable Pre-released updates in Software sources > updates

---

### Post by Shazaam on 2008-08-13
Remember, files in the "Pre-Released" repo are just that. Consider them Alpha/Beta apps and YOU are the tester. They can break your system as happened with the recent original release of 2.6.24.20. Luckily it was easy to boot to an older kernel to get a working system again.
[https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344)

---

