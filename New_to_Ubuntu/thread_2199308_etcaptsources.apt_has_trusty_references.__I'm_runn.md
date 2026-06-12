---
title: "/etc/apt/sources.apt has trusty references.  I'm running 12.04"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by cwmoser on 2014-01-13
My **/etc/apt/sources.list** has references to trusty - no longer has Precise Pangolin sources.
I have a lot of entries in my sources.list file similar to this:
  deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
  deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
  deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
  deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner

Is this normal or have I did I foo bar something?
I'll admit I was fooling around with these commands:
sudo apt-get dist-upgrade
sudo update-manager -d
sudo do-release-upgrade -d

Can someone post their **sources.list** file?

Thanks

Carl

---

### Post by coffeecat on 2014-01-13
When you ran sudo do-release-upgrade -d, you would have seen a message similar to this awaiting your response:

```
Do you want to start the upgrade? 


13 packages are going to be removed. 151 new packages are going to be 
installed. 1558 packages are going to be upgraded. 

You have to download a total of 817 M. This download should take 
about 7 minutes with your connection. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be cancelled. 

 Continue [yN]  Details [d]

```

At that point your sources.list would have been rewritten with trusty. If you then responded with N, the sources.list file would have been rewritten back to what it was before you ran the command. If you responded with y, then the system would have been upgraded to Trusty, but that would have taken over an hour with a large download.

What was your response, N or y?

What is the contents of your /etc/lsb-release file?

---

### Post by cwmoser on 2014-01-13
Thanks.  I was testing those commands and expecting to enter "N" to upgrade but did not see it.

My /etc/lsb-release file is:

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"

---

### Post by grahammechanical on 2014-01-13
Clear information on the apt-get commands.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by Dave_L on 2014-01-13
Do you have this file? /etc/apt/sources.list.save

---

### Post by coffeecat on 2014-01-13
> **cwmoser said:**
> Thanks.  I was testing those commands and expecting to enter "N" to upgrade but did not see it.

My /etc/lsb-release file is:

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"

That indicates that you probably haven't been upgraded. FWIW, here's the sources.list file from a somewhat neglected Precise install:

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120419)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120419)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120419)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

If you want to be absolutely sure you don't have a partially upgraded system, running uname -a will tell you the kernel version in use. For my up-to-date Trusty install it's currently 3.13.0-2-generic

---

### Post by cwmoser on 2014-01-13
Thanks for the sources.list file.

On my 12.04, I have:
$ uname -a
Linux klaatu-2 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by monkeybrain20122 on 2014-01-13
> **coffeecat said:**
> When you ran sudo do-release-upgrade -d, you would have seen a message similar to this awaiting your response:

```
Do you want to start the upgrade? 


13 packages are going to be removed. 151 new packages are going to be 
installed. 1558 packages are going to be upgraded. 

You have to download a total of 817 M. This download should take 
about 7 minutes with your connection. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be cancelled. 

 Continue [yN]  Details [d]

```

At that point your sources.list would have been rewritten with trusty. If you then responded with N, the sources.list file would have been rewritten back to what it was before you ran the command. If you responded with y, then the system would have been upgraded to Trusty, but that would have taken over an hour with a large download.

What was your response, N or y?

What is the contents of your /etc/lsb-release file?

Why would "sudo do-release-upgrade -d" upgrades to Trusty, which is not even released??!! I would think that if OP ran the command (which he didn't apparently) and answered "yes" it would have been upgraded to Saucy. Am I missiing something?

---

### Post by oldos2er on 2014-01-13
The "-d" variable checks for the latest development release, which in this case is Trusty.

---

### Post by coffeecat on 2014-01-13
> **monkeybrain20122 said:**
> Am I missiing something?

Yes.

From man do-release-upgrade:

```
-d, --devel-release
              Check if upgrading to the latest devel release is possible
```

---

### Post by monkeybrain20122 on 2014-01-13
Oh I see. Thanks.

---

