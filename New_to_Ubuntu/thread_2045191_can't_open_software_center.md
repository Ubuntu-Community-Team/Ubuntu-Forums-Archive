---
title: "can't open software center"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by amrosama77 on 2012-08-20
every time I open it ,it just start to load then auto close !!!

any advice...?

---

### Post by Bashing-om on 2012-08-20
am--77 Hi !

 OK, do you have connectivity to the internet ?
If so .... from your file browser go to /etc/apt/sources.list .
doubleclick the sources.list icon , input password..
  1. what sources do you have ticked ?
  2. in the "Download from" window do you have a mirror sited ?

also what version of ubuntu are you running ? as my system sited is 10.04.

 let us know 
[INDENT]kindest regards <==BDQ
[/INDENT]

---

### Post by amrosama77 on 2012-08-21
Yes I have internet connection,
when I double clicked the sources.list file it didn't ask for my password it just opened and here is the content >>>>
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise universe
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner


>>>>>>>>>>>
>> in the "Download from" window do you have a mirror sited ?
sorry I don't understand what do you mean by this 

I am on ubuntu 12

Thank you for helping me out

---

### Post by NikTh on 2012-08-21
Hi , 
try to reinstall sofware-center and update it. 
```
sudo apt-get install --reinstall software-center
sudo update-software-center
``` 
Thanks

---

### Post by raja.genupula on 2012-08-21
open your terminal and type this 

```
software-center
``` and post the errors.

---

### Post by amrosama77 on 2012-08-21
I solve my problem by deleting those two lines >>

deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

---

### Post by NikTh on 2012-08-21
> **amrosama77 said:**
> 
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

Above lines seems mismatched here , not below 
> **amrosama77 said:**
> I solve my problem by deleting those two lines >>

deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

Thanks.

---

