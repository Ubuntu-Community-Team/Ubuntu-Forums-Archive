---
title: "Broken Packages error While Installing dependencies for Ruby"
date: 2016-01-11
forum: New to Ubuntu
---

### Post by vigneshwaran2 on 2016-01-11
I am trying to install Ruby 2.2.3 version, so i was using the guide from [URL="https://gorails.com/setup/ubuntu/14.04"]https://gorails.com/setup/ubuntu/14.04 and as it shows the first step to install some dependencies for ruby. So I tried 
[/URL]$sudo apt-get update
$sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev

But I got the following error.

```
$sudo apt-get install zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
 libcurl4-openssl-dev : Depends: libcurl3 (= 7.35.0-1ubuntu2.3) but 7.35.0-1ubuntu2.5 is to be installed
                        Depends: libkrb5-dev but it is not going to be installed
                        Depends: libldap2-dev but it is not going to be installed
                        Depends: librtmp-dev but it is not going to be installed
 libsqlite3-dev : Depends: libsqlite3-0 (= 3.8.2-1ubuntu2) but 3.8.2-1ubuntu2.1 is to be installed
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1f-1ubuntu2.8) but 1.0.1f-1ubuntu2.15 is to be installed
              Recommends: libssl-doc but it is not going to be installed
 sqlite3 : Depends: libsqlite3-0 (= 3.8.2-1ubuntu2) but 3.8.2-1ubuntu2.1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

How can I solve this, What is the error? Please I am new to ubuntu and I need someone to help me. Thank you.

---

### Post by ian-weisser on 2016-01-11
Looks very much like a *version conflict*.
Some parts of your system depend upn version A of a package. Other parts depend upon version B.
You can have only one version (A) installed at a time. The parts that depend upon version B *conflict*.
That's what the error message meant by "You have requested an impossible situation"

The most common cause of a version conflict is a non-Ubuntu software source. Ubuntu sources are built from the proper versions.

> **vigneshwaran2 said:**
> libcurl4-openssl-dev : Depends: libcurl3 (= 7.35.0-1ubuntu2.3) but 7.35.0-1ubuntu2.5 is to be installed
                        
Here's an example: Part of your system requires libcurl version 7.35.0-1ubuntu2.**3**, but the proper version required by your system should is 7.35.0-1ubuntu2.**5**.

It's usually easy to fix: We identify and uninstall the conflicting software, and autoremove it's conflicting dependencies. Compatible software is uaually availble.

Please show us the complete output of the following command:
```
apt-cache policy libcurl3
```

---

### Post by vigneshwaran2 on 2016-01-11
The output for your mentioned command is

```
libcurl3:
  Installed: 7.35.0-1ubuntu2.5
  Candidate: 7.35.0-1ubuntu2.5
  Version table:
 *** 7.35.0-1ubuntu2.5 0
        100 /var/lib/dpkg/status
     7.35.0-1ubuntu2.3 0
        500 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-updates/main i386 Packages
        500 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-security/main i386 Packages
     7.35.0-1ubuntu2 0
        500 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty/main i386 Packages
```

---

### Post by Geoffrey_Arndt on 2016-01-11
Might take a look at the Brightbox team's PPA/server . . . but is a testing version:

[https://launchpad.net/~brightbox/+archive/ubuntu/ruby-ng-experimental](https://launchpad.net/~brightbox/+archive/ubuntu/ruby-ng-experimental)

---

### Post by vigneshwaran2 on 2016-01-11
thanks dude, I can consider that, but what's the reason for that error.

---

### Post by sandyd on 2016-01-11
Hi, can you post the output of the following:

```

grep "" /etc/apt/sources.list.d/*
apt-get -s install g++=4:4.8.2-1ubuntu6

```

---

### Post by vigneshwaran2 on 2016-01-11
Here's the output for the above code.
```

vicky@hiblue:~$ grep "" /etc/apt/sources.list.d/*
deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main
vicky@hiblue:~$ apt-get -s install g++=4:4.8.2-1ubuntu6
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 g++ : Depends: g++-4.8 (>= 4.8.2-5~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

---

### Post by sandyd on 2016-01-11
What about...
```

cat /etc/apt/sources.list
apt-get -s install g++=4:4.8.2-1ubuntu6 g++-4.8=4.8.4-2ubuntu1~14.04

```

---

### Post by ian-weisser on 2016-01-11
> **vigneshwaran2 said:**
> [...] what's the reason for that error.

Your source at ubuntu.excellmedia.net seems to have old packages.
See your output below.

> **vigneshwaran2 said:**
> 
  Version table:
 *** 7.35.0-1ubuntu**2.5 0**
        100 /var/lib/dpkg/status
     7.35.0-1ubuntu**2.3 0**
        500 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-updates/main i386 Packages
        500 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty-security/main i386 Packages
     7.35.0-1ubuntu2 0
        500 [http://ubuntu.excellmedia.net/archive/](http://ubuntu.excellmedia.net/archive/) trusty/main i386 Packages

That's rather confusing. I wonder how your system downloaded 2.5 if your source mirror only has 2.3.
Perhaps try a different mirror.

---

### Post by vigneshwaran2 on 2016-01-11
I Got...
```
vicky@hiblue:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta i386 (20150805)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.excellmedia.net/archive/ trusty main restricted
deb-src http://ubuntu.excellmedia.net/archive/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.excellmedia.net/archive/ trusty-updates main restricted
deb-src http://ubuntu.excellmedia.net/archive/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.excellmedia.net/archive/ trusty universe
deb-src http://ubuntu.excellmedia.net/archive/ trusty universe
deb http://ubuntu.excellmedia.net/archive/ trusty-updates universe
deb-src http://ubuntu.excellmedia.net/archive/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.excellmedia.net/archive/ trusty multiverse
deb-src http://ubuntu.excellmedia.net/archive/ trusty multiverse
deb http://ubuntu.excellmedia.net/archive/ trusty-updates multiverse
deb-src http://ubuntu.excellmedia.net/archive/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.excellmedia.net/archive/ trusty-backports main restricted universe multiverse
deb-src http://ubuntu.excellmedia.net/archive/ trusty-backports main restricted universe multiverse

deb http://ubuntu.excellmedia.net/archive/ trusty-security main restricted
deb-src http://ubuntu.excellmedia.net/archive/ trusty-security main restricted
deb http://ubuntu.excellmedia.net/archive/ trusty-security universe
deb-src http://ubuntu.excellmedia.net/archive/ trusty-security universe
deb http://ubuntu.excellmedia.net/archive/ trusty-security multiverse
deb-src http://ubuntu.excellmedia.net/archive/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

vicky@hiblue:~$ apt-get -s install g++=4:4.8.2-1ubuntu6 gcc=4:4.8.2-1ubuntu6
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 g++ : Depends: g++-4.8 (>= 4.8.2-5~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by vigneshwaran2 on 2016-01-11
I need to update some stuff through mirror?

---

### Post by Geoffrey_Arndt on 2016-01-11
Have you asked Chris Oliver?

---

### Post by vigneshwaran2 on 2016-01-11
Sorry, I can't get you.

---

### Post by sandyd on 2016-01-11
Go to Ubuntu Software Center -> Click on Edit, and choose software sources.

Change "Download from:" to "Main  Server", and enter your password when it asks.

Go back to the terminal, and try installation commands again after running
```

sudo apt-get update
```

---

### Post by vigneshwaran2 on 2016-01-12
Thanks Sandyd, It worked.:D

---

