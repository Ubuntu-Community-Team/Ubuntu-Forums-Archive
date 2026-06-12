---
title: "How to install the latest Nvidia drivers on Ubuntu 14.04 Trusty Tahr"
date: 2015-01-26
forum: New to Ubuntu
---

### Post by mdavis1231 on 2015-01-26
I'm just now coming back to Ubuntu after about a year, and have installed 14.04 LTS Trusty Tahr on my laptop.  Always before, my Ubuntu would inform me that there were proprietary drivers available, and I would choose the best one and install it.  However, Trusty Tahr is not informing me that there are any propriety drivers available.  I found this article:  

[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/) 

- and I've ran the command line that it told me to.  Here is the outcome.  I'm wondering if it's safe to install the xorg-edgers ppa, and if so, which Nvidia driver that I should choose.  I don't want to do anything whatsoever to ruin my OS, but I also want to make it the very best that I can.  Anyone have any advice on what would be the best route for me to take?  Thanks a lot!!!

---

### Post by Bucky Ball on 2015-01-26
Welcome back. Before installing the xorg-edgers PPA, have you done an update? If not, do one then check in Additional Drivers (might be Hardware Drivers in your release).

---

### Post by deadflowr on 2015-01-27
There will be no available drivers notification for the card you have shown --ATI Raedeon HD 4225/4250, because ATI(AMD) dropped support for that card.
(Along with all cards below the 5000 series.)

So even xorg-edgers won't help, except to grab newer open-source drivers, maybe.
But you can't install the proprietary drivers for it on trusty.

(Also I hope you realize there is a disconnect between your posting about nvidia and the output of your screenshot=ati)

---

### Post by Bucky Ball on 2015-01-27
> **deadflowr said:**
> There will be no available drivers notification for the card you have shown --ATI Raedeon HD 4225/4250, because ATI(AMD) dropped support for that card.
(Along with all cards below the 5000 series.)

So even xorg-edgers won't help, except to grab newer open-source drivers, maybe.
But you can't install the proprietary drivers for it on trusty.



Tnx for that info, deadflowr. Noted. ;)

---

