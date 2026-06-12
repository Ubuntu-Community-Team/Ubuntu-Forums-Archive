---
title: "SSD configuration"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by betic on 2013-05-14
I have a  240 Gbyte OCZ SSD an a 1 Terabyte WD HDD.  Please point me to "best practices" guide on how to configure Ubuntu 13.04  on a SSD as the host OS running VMware Workstaion 9.  Interested in installation, configuration and backup when using these devices.

---

### Post by prodigy_ on 2013-05-14
Some useful guides and tips here:
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Automatic-TRIM:-by-rc.local-by-cron-or-by-discard](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Automatic-TRIM:-by-rc.local-by-cron-or-by-discard)
[http://askubuntu.com/questions/282831/what-is-recommended-as-optimal-ssdhdd-setup-for-ubuntu](http://askubuntu.com/questions/282831/what-is-recommended-as-optimal-ssdhdd-setup-for-ubuntu)
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
[http://askubuntu.com/questions/78971/best-etc-fstab-setings-for-boosting-ssd-hdd](http://askubuntu.com/questions/78971/best-etc-fstab-setings-for-boosting-ssd-hdd)

With a 240GB SSD you don't have to worry that much about wear [even if it's made of TLC NAND](http://www.anandtech.com/show/6459/samsung-ssd-840-testing-the-endurance-of-tlc-nand). Basic rules (such as mounting with **noatime**) still apply of course.

---

### Post by betic on 2013-05-15
Thanks for the links.

---

### Post by DuckHook on 2013-05-15
I have almost exactly the same config and answered this question some months ago. No point in my repeating myself, so [here's]("http://ubuntuforums.org/showthread.php?p=12494671#post12494671") the link.

---

