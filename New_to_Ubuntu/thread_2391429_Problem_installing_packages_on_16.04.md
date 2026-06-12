---
title: "Problem installing packages on 16.04"
date: 2018-05-09
forum: New to Ubuntu
---

### Post by zunaidz on 2018-05-09
i can't install any app on my ubuntu 16.04
what can i do?

it says:

zunaid@ii:~$ sudo apt-get -f install
[sudo] password for zunaid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 avro : Depends: gjs but it is not installed
        Depends: libibus-1.0-dev but it is not installed
        Depends: ibus-clutter but it is not installed
        Depends: ibus-qt4 but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
zunaid@ii:~$

---

### Post by Autodave on 2018-05-09
Have you made sure that your updates are all done and current?  In a terminal run:

sudo apt-get update
sudo apt-get upgrade

---

### Post by QIII on 2018-05-09
Hello, zunaidz!

Please use meaningful titles for your threads.  I have changed this one for you.

---

### Post by oldrocker99 on 2018-05-09
Things might bet better if you enter:
```
sudo apt -f install
```

---

### Post by zunaidz on 2018-05-09
[COLOR=#ff0000]&#8203;It shows:[/COLOR]


zunaid@zunaid-X542UQ:~$ sudo apt -f install
[sudo] password for zunaid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 avro : Depends: gjs but it is not installed
        Depends: libibus-1.0-dev but it is not installed
        Depends: ibus-clutter but it is not installed
        Depends: ibus-qt4 but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
zunaid@zunaid-X542UQ:~$

---

### Post by zunaidz on 2018-05-09
**[COLOR=#ff0000]&#8203;It shows:[/COLOR]**

zunaid@zunaid-X542UQ:~$ sudo apt-get update
\[sudo] password for zunaid: 
Sorry, try again.
[sudo] password for zunaid: 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                 
Hit:3 [http://bd.archive.ubuntu.com/ubuntu](http://bd.archive.ubuntu.com/ubuntu) bionic InRelease                 
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [69.9 kB]
Hit:6 [http://bd.archive.ubuntu.com/ubuntu](http://bd.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:7 [http://bd.archive.ubuntu.com/ubuntu](http://bd.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Fetched 69.9 kB in 1s (36.8 kB/s)                              
Reading package lists... Done
zunaid@zunaid-X542UQ:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 avro : Depends: gjs but it is not installed
        Depends: libibus-1.0-dev but it is not installed
        Depends: ibus-clutter but it is not installed
        Depends: ibus-qt4 but it is not installed
E: Unmet dependencies. Try using -f.
zunaid@zunaid-X542UQ:~$

---

