---
title: "Problem installing sun java 1.5 jdk"
date: 2006-06-16
forum: Repositories &amp; Backports
---

### Post by linux_developer on 2006-06-16
Hi all,

I am trying to install sun java 1.5jdk. I read the forums and wiki and have enabled the multiverse repository, reloaded synaptic (in fact restarted ubuntu even), changed all my repositories' location from being local (.au) to the main repository (remove .au). 

However whenever I try to search for sun, java, jdk, etc. using synaptic and apt-get, I cannot find the jdk for download. Has it been removed from the repositories?

Thanks,
linux_developer

---

### Post by Delkster on 2006-06-16
No, it's there. The exact name of the package is sun-java5-jdk. Could you post your /etc/apt/sources.list file? Maybe there's something wrong there.

---

### Post by linux_developer on 2006-06-16
This is my file:



deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by sparty2809 on 2006-07-07
I am getting the same problem.  My repositories are the same.  Any help?  Did you figure this out?

---

### Post by sparty2809 on 2006-07-07
I got it to work.  I changed this
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

to 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

---

### Post by Jamo2 on 2006-07-12
This can be fixed by adding: 'multiverse' to the end of every line in your sources.list file that already contains universe

---

