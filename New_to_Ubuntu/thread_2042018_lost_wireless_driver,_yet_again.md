---
title: "lost wireless driver, yet again"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by a77ssii on 2012-08-13
I have an HP Pavilion g series, RealTek RTL819X wireless card running Lucid on the "latest and greatest" kernel.  Problem is as soon as I manage to get my wireless back up another update comes along and wipes it out back to square 1.  The wireless has worked with Lucid on this box and I didn't change anything other than download and install the updates.  At this juncture unless there is a quick and painless fix for it that will STAY with the future updates I'm probably going to migrate to another Linux based O/S other than Ubuntu.  It seems that with every update more and more things quite working that I have to attempt to fix.  I am by no means an expert and rely on my books to get me through it but am tired of spending 4-6 hours every 3 weeks trying to fix something.

---

### Post by wildmanne39 on 2012-08-13
If you had good directions they would have told you when an upgrade to the kernel happens with a driver you complied you would have to compile it again but it is easier the second time just change into the driver directory and do:
```
sudo su
make clean
make
make install
modprobe drivername
exit
```
Thanks

---

