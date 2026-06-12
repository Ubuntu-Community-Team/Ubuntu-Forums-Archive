---
title: "New to Ubunutu - but can't install software now as 'lsb-base is not ready'"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by ta5ah on 2013-04-13
Hi all

brand new to it today, succesful install and everything was going ok. But now I'm trying add new software through Ubuntu Software Centre and I get presented this error when attempting to install. It happens for different programs, e.g. VLC and Chromium.


package lsb-base is not ready for configuration 
 cannot configure (current status `half-installed')


Any ideas how I can resolve this? Sometimes it asks if it's OK to fix itself, but it doesn't succeed.

Thanks

---

### Post by grahammechanical on 2013-04-13
Try running this command to install it.

```
sudo apt-get install lsb-base
```

When I run that command on my machine I get told that I already have the newest version installed. You might get a different response.

or 

```
sudo apt-get -f install
```

to fix broken packages.

Regards.

---

### Post by ta5ah on 2013-04-14
This worked! Thank you for your help. Chromium is now running.

---

