---
title: "[SOLVED] issue with Virtual box....."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by hufferd on 2008-06-07
I had Virtualbox up and running with no issues 

Now I get an error message that says a driver is not installed but it is thats how I got it to work the first time 

any Ideas I have also posted a screen shot of the wrror



D

---

### Post by Oldsoldier2003 on 2008-06-07
> **hufferd said:**
> I had Virtualbox up and running with no issues 

Now I get an error message that says a driver is not installed but it is thats how I got it to work the first time 

any Ideas I have also posted a screen shot of the wrror



D

```
sudo apt-get install virtualbox-ose-modules$(uname -r)
``` if you get an error saying that it cant be found (ie you are using the -18 kernel) you'll need to install the puel version from the virtualbox website

---

### Post by wolfen69 on 2008-06-07
go to synaptic and search for virtualbox-ose-modules and install.

---

### Post by avtolle on 2008-06-07
Take a look at:
[http://ubuntuforums.org/showthread.php?t=813448](http://ubuntuforums.org/showthread.php?t=813448)
also, as it may help you.

---

### Post by Oldsoldier2003 on 2008-06-07
> **avtolle said:**
> Take a look at:
[http://ubuntuforums.org/showthread.php?t=813448](http://ubuntuforums.org/showthread.php?t=813448)
also, as it may help you.

IIRC the ose version doesn't support module compilation from /etc/init.d

In any case the puel version available on their website is more current and has a better feature set than the OSE version available in the repos.

---

