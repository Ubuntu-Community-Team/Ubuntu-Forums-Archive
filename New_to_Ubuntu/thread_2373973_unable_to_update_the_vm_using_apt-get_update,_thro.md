---
title: "unable to update the vm using apt-get update, throwing 403 permission denied error"
date: 2017-10-11
forum: New to Ubuntu
---

### Post by kailashms on 2017-10-11
Hi All,

I have 4 Ubuntu 1604 boxes and when i want to install any package it tells , 403 forbidden error.
we have tried to run below commands
```
#apt-get clean
#cd /var/lib/apt
mv lists lists_old
mkdir -p lists/partial
apt-get clean
apt-get update
```

But afte this also we could see the same issue.
We have removed the file and copied the content from a working vm, but still the same.

when we try to install any package we get the following error
```
cat /etc/apt/sources.list|grep "xenial-updates"
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package walinuxagent is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'walinuxagent' has no installation candidate
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt-get search walinuxagent
E: Invalid operation search
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt-get search walinuxagent
E: Invalid operation search
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt search walinuxagent
Sorting... Done
Full Text Search... Done
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt search WALinuxAgent
Sorting... Done
Full Text Search... Done
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt-get install elinks
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package
```

Any assistance on this highly appreciated

Thanks Kailash B

---

### Post by wildmanne39 on 2017-10-11
*Thread moved to **New to Ubuntu for a better fit**.*

---

### Post by ian-weisser on 2017-10-11
> **kailashms said:**
> root@SMULWEBPM2U001:~# apt-get search walinuxagent
E: Invalid operation search

That's not a 403 error.
That is the expected behavior.
apt-get does not have a 'search' function anymore. Use 'apt search' instead.


> **kailashms said:**
> root@SMULWEBPM2U001:~# apt-get install elinks
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package

That's not a 403 error.
Since elinks has been in the Universe repository since before 12.04, check your apt sources to ensure that you have Universe enabled.


If you are getting a 403 error when running 'apt update', then check your apt sources for a typo or an obsolete repo, or try a different repo.

---

### Post by kailashms on 2017-10-12
thanks for that information
but again when you try to  instal the any packages it shows the same error:

```
Reading package lists... Done
 Building dependency tree
 Reading state information... Done
 Package walinuxagent is not available, but is referred to by another package.
 This may mean that the package is missing, has been obsoleted, or
 is only available from another source
 E: Package 'walinuxagent' has no installation candidate
```

Also when you run the apt-get update
we are getting 403 forbiddedn for some repos
why is that

---

### Post by ian-weisser on 2017-10-12
See Post #3 for those answers.

Please use [code] tags for terminal output, to retain the formatting.

If you need help checking your list of sources, then show us the complete contents of /etc/apt/sources/list and of /etc/aptsources/list.d/*...in [code] tags, of course.

---

### Post by kailashms on 2017-10-12
root@SMULWEBPM2U001:~# apt search walinuxagent
Sorting... Done
Full Text Search... Done
root@SMULWEBPM2U001:~#

This is what i am getting when i run search command

---

### Post by kailashms on 2017-10-12
```
root@SMULWEBPM2U001:~# ls -lh /etc/apt/sources.list.d/
total 0
root@SMULWEBPM2U001:~# apt search walinuxagent


## Note, this file is written by cloud-init on first boot of an instance
## modifications made here will not survive a re-bundle.
## if you wish to make changes you can:
## a.) add 'apt_preserve_sources_list: true' to /etc/cloud/cloud.cfg
##     or do the same in user-data
## b.) add sources in /etc/apt/sources.list.d
## c.) make changes to template file /etc/cloud/templates/sources.list.tmpl
 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial main restricted
deb-src [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb-src [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial universe
deb-src [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb-src [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial multiverse
deb-src [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb-src [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
 
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://azure.archive.ubuntu.com/ubuntu/](http://azure.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
```

---

### Post by wildmanne39 on 2017-10-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ian-weisser on 2017-10-12
Try a different mirror.

---

### Post by kailashms on 2017-10-13
tried that one as well.

---

### Post by kailashms on 2017-10-13
can somebody help me getting the solution for this thread it similar to my issue

[https://ubuntuforums.org/showthread.php?t=2348577](https://ubuntuforums.org/showthread.php?t=2348577)

---

### Post by oldos2er on 2017-10-13
Can you copy/paste the actual 403 errors you're seeing?

---

### Post by kailashms on 2017-10-20
any help on this ?

---

### Post by ian-weisser on 2017-10-20
We are waiting for you to answer Post #12.

---

### Post by RobGoss on 2017-10-21
> **kailashms said:**
> Hi All,

I have 4 Ubuntu 1604 boxes and when i want to install any package it tells , 403 forbidden error.
we have tried to run below commands
```
#apt-get clean
#cd /var/lib/apt
mv lists lists_old
mkdir -p lists/partial
apt-get clean
apt-get update
```

But afte this also we could see the same issue.
We have removed the file and copied the content from a working vm, but still the same.

when we try to install any package we get the following error
```
cat /etc/apt/sources.list|grep "xenial-updates"
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package walinuxagent is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'walinuxagent' has no installation candidate
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt-get search walinuxagent
E: Invalid operation search
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt-get search walinuxagent
E: Invalid operation search
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt search walinuxagent
Sorting... Done
Full Text Search... Done
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt search WALinuxAgent
Sorting... Done
Full Text Search... Done
[EMAIL="root@SMULWEBPM2U001"]root@SMULWEBPM2U001[/EMAIL]:~# apt-get install elinks
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package
```

Any assistance on this highly appreciated

Thanks Kailash B



Are you using** sudo** when trying to update the system? try using** sudo apt-get update**

---

### Post by vasa1 on 2017-10-21
> **RobGoss said:**
> Are you using** sudo** when trying to update the system? try using** sudo apt-get update**
OP seems to prefer root for whatever reason.```
root@SMULWEBPM2U001:~# apt search walinuxagent
```

---

