---
title: "Can not see login screen"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by IamJohnHayes on 2008-08-17
Every time i reboot my computer when the login screen comes up all i see is the very top left hand corner of the screen, like the resolution is all jacked up.  I can still log in, at first it was a nice way of stopping people from trying to mess around on my comp but now its anoying.

if it matters,

Ubuntu 8.04 (Upgraded not fresh install)

Thanks

---

### Post by nicedude on 2008-08-17
I am going to assume you are just using the nvidia driver that Ubuntu's restricted driver manager chose automatically. If so I would recomend you try envyng-gtk which is a program that will download and install teh best Nvidia driver it can find for your card.

TO INSTALL
sudo apt-get install envyng-gtk

TO RUN
sudo envyng-gtk

OR 

Applications -> System Tools -> Envy-ng

Then just let it do everything for you :-)

Hope that fixes it for you.

---

