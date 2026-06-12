---
title: "Unable to correct dependencies"
date: 2016-02-27
forum: New to Ubuntu
---

### Post by rahul_singh2 on 2016-02-27
i am faciing same problem since last one month...
I have tried it but still problem not solved...
here is the output i got after using this command..


rahul@rahul-Inspiron-5520:~$ sudo apt-get install -f
[sudo] password for rahul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is installed
 libnl-route-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
rahul@rahul-Inspiron-5520:~$

---

### Post by TheFu on 2016-02-27
a) please use "code tags" for output so things are lined up and easier to read.
b) remove all PPAs from the /etc/apt/* areas.
c) remove any manually installed .deb pacakges
d) try **aptitude update && aptitude upgrade**

See if that fixes things.  Aptitude can be smarter about dependencies.

---

