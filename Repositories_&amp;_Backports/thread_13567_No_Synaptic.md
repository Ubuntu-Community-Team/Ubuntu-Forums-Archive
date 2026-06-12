---
title: "No Synaptic?"
date: 2005-02-01
forum: Repositories &amp; Backports
---

### Post by mcwtlg on 2005-02-01
Upgraded from warty to hoary the other day, all the upgrades went smoothly, following the [http://ubuntuguide.org/](http://ubuntuguide.org/) guide.  Only thing I can see that is missing or wrong is that Synaptic is gone.  Tried to manually download it and got a library missing error (I am sorry I am at work, not at home in front of my Ubuntu box).  I cannot recall the error though.  I know I tried to install the libraries and balked at that.  Apt-get works ok, but Synaptic will not launch.

Any ideas?

This is my sources.list .. not sure what you mean by backported.

 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricte

---

### Post by poofyhairguy on 2005-02-01
[QUOTE=mcwtlg]Upgraded from warty to hoary the other day, all the upgrades went smoothly, following the [http://ubuntuguide.org/](http://ubuntuguide.org/) guide.  Only thing I can see that is missing or wrong is that Synaptic is gone.  Tried to manually download it and got a library missing error (I am sorry I am at work, not at home in front of my Ubuntu box).  I cannot recall the error though.  I know I tried to install the libraries and balked at that.  Apt-get works ok, but Synaptic will not launch.

Any ideas?[/QUOTE]


Did you have the backported version in Warty? that might be what causes the problem.

---

### Post by mcwtlg on 2005-02-04
I think I found my answer on another forum.  Seems like the Hoary packages are incomplete at the moment.

---

