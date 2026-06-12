---
title: "Getting this error in software center when installing brackets"
date: 2015-08-07
forum: New to Ubuntu
---

### Post by kapi on 2015-08-07
Trying to install brackets IDE and got the following message in the software center.

'Dependency is not satisfiable libgcrypt11(>=1.4.5)'

Does this mean the deb file is not able to load in this version of Ubuntu? or do I have to install a missing file?

Thanks

---

### Post by dino99 on 2015-08-07
that means the deb you have downloaded is either not compatible with your ubuntu installation (version mismatch) or its sources is untrusted/unmaintained/....

purge the brackets installation first via the terminal:>  sudo apt-get purge brackets* (i suppose it has been installed with that name, if not select the strict name used)
then add that ppa, and then update: [https://launchpad.net/~webupd8team/+archive/ubuntu/brackets](https://launchpad.net/~webupd8team/+archive/ubuntu/brackets)
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs)

---

