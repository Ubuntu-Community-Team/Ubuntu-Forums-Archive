---
title: "flex and bison package"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by dharmvir tiwari on 2013-01-04
I wanted to know the installation procedure for FLEX and BISON package.
i have tried apt-get install ,but an error is being reported as "package has been renamed"

---

### Post by windscape on 2013-01-04
Hi,

It would help us to determine the cause of your issue if you posted your Ubuntu version, the exact commands you used, and their entire output.

---

### Post by dharmvir tiwari on 2013-01-05
> **windscape said:**
> Hi,

It would help us to determine the cause of your issue if you posted your Ubuntu version, the exact commands you used, and their entire output.
I am using  Ubuntu 12.04

---

### Post by steeldriver on 2013-01-05
That's strange - candidates are showing for me

```
$ apt-cache policy bison flex
bison:
  Installed: (none)
  Candidate: 1:2.5.dfsg-2.1
  Version table:
     1:2.5.dfsg-2.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
flex:
  Installed: (none)
  Candidate: 2.5.35-10ubuntu3
  Version table:
     2.5.35-10ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```
```
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

```
Have you tried doing a [FONT=Courier New]sudo apt-get update[/FONT] first to make sure the package information is current?

---

### Post by dharmvir tiwari on 2013-01-08
> **steeldriver said:**
> That's strange - candidates are showing for me

```
$ apt-cache policy bison flex
bison:
  Installed: (none)
  Candidate: 1:2.5.dfsg-2.1
  Version table:
     1:2.5.dfsg-2.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
flex:
  Installed: (none)
  Candidate: 2.5.35-10ubuntu3
  Version table:
     2.5.35-10ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```
```
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

```
Have you tried doing a [FONT=Courier New]sudo apt-get update[/FONT] first to make sure the package information is current?
i've tried apt-get install flex
But it's not getting install

---

