---
title: "Problem with my ubuntu instalation"
date: 2023-08-11
forum: New to Ubuntu
---

### Post by emdi01 on 2023-08-11
Hello, 


I am not a programer nor have the enough information about programing.
Please help me fix ubuntu on my laptop. 
I have ubuntu 22.04.2 LTS,  I installed ubuntu a few years ago on my laptopt and I think I didn't do it right... 
The problem I have is that I can't install/unstiall or update nothing on my computer. Even when I try to update chrome it lets me install but doesn't apply the update.
I can't uninstall chrome... please help me figure this out.

Thank you!

---

### Post by yancek on 2023-08-11
Ubuntu 22.04 was initially released in April, 2022.  Is that when you first installed Ubuntu? Did you download and install google-chrome from the official site?  Did you install the stable version from the Ubuntu repositories?  Did you try the method suggested at the google site at the link below?

[https://support.google.com/chrome/answer/95414?sjid=9310427460440766451-NA](https://support.google.com/chrome/answer/95414?sjid=9310427460440766451-NA)

---

### Post by Rubi1200 on 2023-08-11
Hi and welcome to the forums :-)

In addition to what yancek suggested, please open a terminal from the menu or with Ctrl+Alt+T and show us the output of these commands:

```
cat /etc/apt/sources.list
```

and also

```
sudo apt update
```

For the second command you only need to copy the part where there are errors, if any.

Copy the output from the terminal and when you reply use Go Advanced option and wrap the text with the # tags for easier reading.

---

### Post by emdi01 on 2023-08-14
##########################################################################

#~$ cat /etc/apt/sources.list# deb cdrom:[Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) jammy main restricted
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) focal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) jammy-updates main restricted
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) focal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) jammy universe
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) focal universe
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) jammy-updates universe
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) focal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) jammy multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) jammy-updates multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) focal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) jammy-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse




deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse


# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
##############################################################

#~$ sudo apt update


#10 packages can be upgraded. Run 'apt list --upgradable' to see them.
#~$ apt list --upgradable
#Listing... Terminat
#gjs/jammy-updates 1.72.4-0ubuntu0.22.04.1 amd64 [upgradable from: 1.72.2-0ubuntu2]
#intel-microcode/jammy-updates,jammy-security 3.20230808.0ubuntu0.22.04.1 amd64 [upgradable from: 3.20230214.0ubuntu0.22.04.1]
#ldap-utils/jammy-updates 2.5.16+dfsg-0ubuntu0.22.04.1 amd64 [upgradable from: 2.5.14+dfsg-0ubuntu0.22.04.2]
#libgjs0g/jammy-updates 1.72.4-0ubuntu0.22.04.1 amd64 [upgradable from: 1.72.2-0ubuntu2]
#libldap-2.5-0/jammy-updates 2.5.16+dfsg-0ubuntu0.22.04.1 amd64 [upgradable from: 2.5.14+dfsg-0ubuntu0.22.04.2]
#libldap-common/jammy-updates,jammy-updates 2.5.16+dfsg-0ubuntu0.22.04.1 all [upgradable from: 2.5.14+dfsg-0ubuntu0.22.04.2]
#linux-generic-hwe-20.04/jammy-updates 5.15.0.79.76 amd64 [upgradable from: 5.15.0.78.75]
#linux-generic/jammy-updates 5.15.0.79.76 amd64 [upgradable from: 5.15.0.78.75]
#linux-headers-generic/jammy-updates 5.15.0.79.76 amd64 [upgradable from: 5.15.0.78.75]
#linux-image-generic/jammy-updates 5.15.0.79.76 amd64 [upgradable from: 5.15.0.78.75]


##################################################################################


Thank you :smile:

---

### Post by emdi01 on 2023-08-14
I don't remember if in april of 2022, I thing I have it installed from 2020 (I may be wrong...:oops:) Yes, I did installed google-chrome from official site :KS

---

### Post by ian-weisser on 2023-08-14
What about other sources in /etc/apt/sources.list.d/ ?

---

