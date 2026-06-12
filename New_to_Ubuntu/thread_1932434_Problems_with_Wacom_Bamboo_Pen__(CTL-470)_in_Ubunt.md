---
title: "Problems with Wacom Bamboo Pen  (CTL-470) in Ubuntu 10.04 LTS"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by disabled20191128 on 2012-02-27
Hi, I am running Ubuntu 10.04 LTS and I am having problems with the Wacom Bamboo Pen Tablet (CTL-470).
I have tried to set it up by running these commands

sudo add-apt-repository ppa:lekensteyn/wacom-tablet
sudo apt-get update
sudo apt-get install wacom-dkms 

but with no success even after reboot.

Please Help Me

---

### Post by Favux on 2012-02-27
Hi Dennisgre,

The Wacom Bamboo Pen Tablet (CTL-470) isn't supported in Lucid yet.

See the stuff on the third generation models on the BambooPT HOW TO near the top:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

Chris has backported support for them in Natty and Oneiric using input-wacom.  He has come up with an initial solution for Lucid, see appendix 2 near the bottom of the HOW TO.  When he gets some tester feedback that it works he plans to add the Lucid support to input-wacom.

---

### Post by disabled20191128 on 2012-02-28
Thank you Favux for your reply, I guess that I will have to upgrade my system to 11.04 !!

---

### Post by Favux on 2012-02-28
If you're going to upgrade your release I'd go for Oneiric (11.10).  Unity is improve in it over Natty.  Plus Precise will be out in two months and an update to it would be easier then.

---

### Post by disabled20191128 on 2012-03-10
OK thank you very much

---

