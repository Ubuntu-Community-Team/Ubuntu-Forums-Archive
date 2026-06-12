---
title: "php5 / mysql installation problem"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by marufaberlin on 2008-05-25
Hi,

Somehow I can't install mysql, but maybe yo'd better see for yourself...
```

$ sudo apt-get install php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  php5-mysql: Depends: php5-common (= 5.2.3-1ubuntu6) but 5.2.3-1ubuntu6.3 is to be installed
E: Broken packages

```what should I do?

---

### Post by shifty_powers on 2008-05-25
by the looks of it, the package you are trying to download requires a package that is no longer in the hardy repo's, seemingly being replacd with an updated one.

you can look in

[http://packages.ubuntu.com](http://packages.ubuntu.com)

for php5-common 5.2.3-1ubuntu6

---

### Post by bodhi.zazen on 2008-05-25
try :

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Then try re-installing.

---

### Post by marufaberlin on 2008-05-30
I can't update due to this problem: [http://ubuntuforums.org/showthread.php?t=739060](http://ubuntuforums.org/showthread.php?t=739060)

---

