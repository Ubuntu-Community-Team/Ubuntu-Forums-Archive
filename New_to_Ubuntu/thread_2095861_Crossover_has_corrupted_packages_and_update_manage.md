---
title: "Crossover has corrupted packages and update manager on Ubuntu 12.04 64bit"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by rd79 on 2012-12-16
I attempted to install crossover_11.3.1-1_i386.deb on Ubuntu 12.04 64bit today and it's stuck on below error...i;m unable to correct errors....can anyone help me please

I attempted to remove and/or correct from within Synaptic, no progress. Synaptic keeps asking me to resolve dependencies/fix broken packages before it will install or remove anything further.

rd@RDBytes:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 crossover:i386 : Depends: perl5-base:i386
                  Depends: perl-modules:i386 but it is not installable
                  Depends: python:i386 (>= 2.4) but it is not installed
                  Depends: python-gtk2:i386 but it is not installed
                  Depends: python-glade2:i386 but it is not installed
                  Depends: desktop-file-utils:i386 but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by squakie on 2012-12-16
Scratch what I had here - it was wrong.  I installed crossover in 64-bit 12.04 ok - mine is ia32-crossover_11.3.0-1_amd64.deb  - I don't know - perhaps you don't have the 64-bit version?

---

### Post by Mr. Hibba on 2012-12-17
> **rd79 said:**
> I attempted to install crossover_11.3.1-1_i386.deb on Ubuntu 12.04 64bit today and it's stuck on below error...i;m unable to correct errors....can anyone help me please

I attempted to remove and/or correct from within Synaptic, no progress. Synaptic keeps asking me to resolve dependencies/fix broken packages before it will install or remove anything further.

rd@RDBytes:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 crossover:i386 : Depends: perl5-base:i386
                  Depends: perl-modules:i386 but it is not installable
                  Depends: python:i386 (>= 2.4) but it is not installed
                  Depends: python-gtk2:i386 but it is not installed
                  Depends: python-glade2:i386 but it is not installed
                  Depends: desktop-file-utils:i386 but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


Hi, and welcome to the Ubuntu forums!  As a general guideline, please start a new thread if you are experiencing a different issue than the original poster.  

That particular version of Crossover is out of date.  I would recommend getting the new .deb version (currently at 12.0.0) directly from Codeweavers ([http://www.codeweavers.com](http://www.codeweavers.com)).

Mr. Hibba

---

### Post by rd79 on 2012-12-18
Thannks Mr. Hibba. At the moment i'm neither able to remove nor install additional packages of any sort through terminal, ubuntu software center or synaptic. Any clue how i can remove packages.

Error i receive today is 
The following packages have unmet dependencies:
 crossover:i386 : Depends: perl5-base:i386
                  Depends: perl-modules:i386 but it is not installable
                  Depends: python:i386 (>= 2.4) but it is not installed
                  Depends: python-gtk2:i386 but it is not installed
                  Depends: python-glade2:i386 but it is not installed
                  Depends: desktop-file-utils:i386 but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by rd79 on 2012-12-18
I attempted to install crossover_11.3.1-1_i386.deb on Ubuntu 12.04 64bit today and it's stuck on below error...i;m unable to correct errors....can anyone help me please

I attempted to remove and/or correct from within Synaptic, no progress. Synaptic keeps asking me to resolve dependencies/fix broken packages before it will install or remove anything further.

rd@RDBytes:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
crossover:i386 : Depends: perl5-base:i386
Depends: perl-modules:i386 but it is not installable
Depends: python:i386 (>= 2.4) but it is not installed
Depends: python-gtk2:i386 but it is not installed
Depends: python-glade2:i386 but it is not installed
Depends: desktop-file-utils:i386 but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by audiomick on 2012-12-18
This

> **rd79 said:**
> 
                  Depends: python:i386 (>= 2.4) but it is not installed
                

can be difficult. The program you are trying to install wants a newer version of a package than the one installed. If the newer one is not in the repositories, you have to risk breaking your system by installing the newer one (and figure out how to do that...) which might have follow on effects on other packages. 

Having said that, this 10.04 install has Python v.2.6 in the repos. Have you looked in the software centre to see if there is any python installed at all, and if so, which version?


Mr. Hibba suggested you get a more current version on crossover. Have you tried that?


Regarding this
> At the moment i'm neither able to remove nor install additional packages of any sort 

you mean you can't install anything at all, even packages that have nothing to do with crossover? 

First thing is to make sure your internet connection is ok. Second is the chance that the server your machine is trying to connect to has a problem. Try again later is the first step.

When neither of those can be suspected:

Firstly, do you make sure that you only have one program at a time running that is using apt, i.e. you can't have synaptic and the software centre running at the same time, you can't use apt-get in the terminal when either of those is open, you can't use any of them if the update manager is waiting for you to confirm and update.

If you think that apt might be confused, you could try the following commands.

```
sudo dpkg --configure -a
```
causes packages that are waiting to be configured to be configured.
Look at 
```
man dpkg
```

to read about dpkg, or
```
dpkg --help
```

Then, 
```
sudo apt-get update
```

causes the package list to be updated

and then
```
sudo apt-get upgrade
```

cause all installed packages to be updated to the latest version available. This is not a version upgrade of the OS. That is a different option on apt-get.

For more on apt-get
```
man apt-get
```

---

### Post by sffvba[e0rt on 2012-12-18
*Posts from other thread **merged** with this thread.*


404

---

### Post by rd79 on 2013-01-03
> **audiomick said:**
> This



can be difficult. The program you are trying to install wants a newer version of a package than the one installed. If the newer one is not in the repositories, you have to risk breaking your system by installing the newer one (and figure out how to do that...) which might have follow on effects on other packages. 

Having said that, this 10.04 install has Python v.2.6 in the repos. Have you looked in the software centre to see if there is any python installed at all, and if so, which version?


Mr. Hibba suggested you get a more current version on crossover. Have you tried that?


Regarding this


you mean you can't install anything at all, even packages that have nothing to do with crossover? 

First thing is to make sure your internet connection is ok. Second is the chance that the server your machine is trying to connect to has a problem. Try again later is the first step.

When neither of those can be suspected:

Firstly, do you make sure that you only have one program at a time running that is using apt, i.e. you can't have synaptic and the software centre running at the same time, you can't use apt-get in the terminal when either of those is open, you can't use any of them if the update manager is waiting for you to confirm and update.

If you think that apt might be confused, you could try the following commands.

```
sudo dpkg --configure -a
```
causes packages that are waiting to be configured to be configured.
Look at 
```
man dpkg
```

to read about dpkg, or
```
dpkg --help
```

Then, 
```
sudo apt-get update
```

causes the package list to be updated

and then
```
sudo apt-get upgrade
```

cause all installed packages to be updated to the latest version available. This is not a version upgrade of the OS. That is a different option on apt-get.

For more on apt-get
```
man apt-get
```
Yes, i cannot install or remove any package from my system. I have gone through your suggestions and have attempting through Synaptic, Apt & USC individually/seperately/one-software-at-a-time, nothing seems to be help.

---

