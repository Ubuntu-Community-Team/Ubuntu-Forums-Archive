---
title: "Error when running command sudo apt-get install -f"
date: 2017-12-18
forum: New to Ubuntu
---

### Post by zmckool on 2017-12-18
Hi, I am new to Linux. I am stuck at this point, because I can't seem to install anything without it asking for me to "Try 'apt-get -f install'". Any help will be greatly appreciated. Thank you in advance. 

```
zack@G751JT:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libc6-dev-i386
The following NEW packages will be installed:
  libc6-dev-i386
0 upgraded, 1 newly installed, 0 to remove and 232 not upgraded.
130 not fully installed or removed.
Need to get 0 B/1,262 kB of archives.
After this operation, 6,936 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 249252 files and directories currently installed.)
Preparing to unpack .../libc6-dev-i386_2.23-0ubuntu9_amd64.deb ...
Unpacking libc6-dev-i386 (2.23-0ubuntu9) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu9_amd64.deb (--unpack):
 trying to overwrite '/usr/include/sys/uio.h', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu9
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


```
zack@G751JT:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu9) but it is not going to be installed
 software-center : Depends: software-center-aptdaemon-plugins but it is not going to be installed
                   Depends: gir1.2-gmenu-3.0 (>= 3.1.5) but it is not going to be installed
                   Depends: python-gi (>= 3.4.0-1ubuntu0.1) but it is not going to be installed
                   Depends: python-gi-cairo but it is not going to be installed
                   Depends: python-xapian
                   Depends: python-aptdaemon (>= 0.40) but it is not going to be installed
                   Depends: python-aptdaemon.gtk3widgets but it is not going to be installed
                   Depends: python-dbus but it is not going to be installed
                   Depends: python-defer but it is not going to be installed
                   Depends: python-lxml but it is not going to be installed
                   Depends: python-xdg but it is not going to be installed
                   Depends: ubuntu-sso-client but it is not going to be installed
                   Depends: python-piston-mini-client (>= 0.1+bzr29) but it is not going to be installed
                   Depends: oneconf (>= 0.2.6) but it is not going to be installed
                   Depends: python-oneconf (>= 0.3) but it is not going to be installed or
                            oneconf (< 0.3) but it is not going to be installed
                   Depends: python-debtagshw but it is not going to be installed
                   Recommends: apt-xapian-index (>= 0.38ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by Bashing-om on 2017-12-18
zmckool; Ouch ..

Putting the carriage before the horse:
> 
0 to remove and 232 not upgraded.


what results with the upgrade process:
```

sudo apt update
sudo apt full-upgrade

```

depending here is what is done next.

[INDENT][INDENT]there is that process
[/INDENT][/INDENT]

---

### Post by zmckool on 2017-12-18
Bashing-om, thank you for your reply. Here is what I get when I run those commands. Again, thank you in advance. I am guessing I have to install the libc6 dependency? 

```
zack@G751JT:~$ sudo apt update
[sudo] password for zack: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://repo.steampowered.com/steam precise InRelease                     
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:4 http://ppa.launchpad.net/apandada1/brightness-controller/ubuntu xenial InRelease
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Fetched 306 kB in 0s (380 kB/s)                                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
232 packages can be upgraded. Run 'apt list --upgradable' to see them.


```

```
zack@G751JT:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu9) but it is not installed
E: Unmet dependencies. Try using -f.


```

---

### Post by Bashing-om on 2017-12-18
zmckooll Yeah :)

That is a reasonable assumption .

But I must inquire why you are installing development packing when you do not understand the package management system .

Is there really a need ?
see:
```

apt show libc6-dev-i386

```

However, we are here to help - but not to break a system.

[INDENT][INDENT]there is a way that seems right .... But[/INDENT][/INDENT]

---

### Post by zmckool on 2017-12-18
Hey Bashing-om,

I am trying to install this because no matter what I install I get this error. Also, when I try to update Linux, a window pops up that says this "The  package system is broken: Check if you are using third party  repositories. If so disable them, since they are a common source of  problems. Furthermore run the following command in a Terminal: apt-get  install -f".


```
zack@G751JT:~$ sudo apt-get install brightness-controller-simple
[sudo] password for zack: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 brightness-controller-simple : Depends: python-wxgtk3.0 but it is not going to be installed or
                                         python-wxgtk2.8 but it is not installable or
                                         python-wxgtk2.6 but it is not installable
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu9) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
zack@G751JT:~$ 


```

```
zack@G751JT:~$ apt show libc6-dev-i386
Package: libc6-dev-i386
Version: 2.23-0ubuntu9
Priority: optional
Section: libdevel
Source: glibc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 6,936 kB
Provides: lib32c-dev
Depends: libc6-i386 (= 2.23-0ubuntu9), libc6-dev (= 2.23-0ubuntu9)
Recommends: gcc-multilib
Homepage: http://www.gnu.org/software/libc/libc.html
Supported: 5y
Download-Size: 1,262 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Description: GNU C Library: 32-bit development libraries for AMD64
 Contains the symlinks and object files needed to compile and link programs
 which use the standard C library. This is the 32bit version of the
 library, meant for AMD64 systems.

N: There is 1 additional record. Please use the '-a' switch to see it
zack@G751JT:~$ 


```

---

### Post by Bashing-om on 2017-12-18
zmckool; Humm ..

"brightness-controller-simple" is not in our software repository, where and how are you getting it ?

Let's put it in the back of our minds that we may have to have a talk with the PPA maintainer ?
show:
```

apt policy brightness-controller-simple

```

Maybe there is a better means to this end ?

[INDENT][INDENT]yukkie
[/INDENT][/INDENT]

---

### Post by zmckool on 2017-12-18
Bashing-om, I was following the directions here [https://askubuntu.com/questions/762764/cant-change-brightness-in-ubuntu-16-04-lts](https://askubuntu.com/questions/762764/cant-change-brightness-in-ubuntu-16-04-lts).

```
zack@G751JT:~$ apt policy brightness-controller-simple
brightness-controller-simple:
  Installed: (none)
  Candidate: 1.2.3
  Version table:
     1.2.3 500
        500 http://ppa.launchpad.net/apandada1/brightness-controller/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/apandada1/brightness-controller/ubuntu xenial/main i386 Packages
zack@G751JT:~$ 


```

---

### Post by Bashing-om on 2017-12-18
zmckool; Ho kay

Is a reputable  developer and he does maintain his PPAs .

But what is your goal here that a simple xrandr command does not meet the need ?
I do endorse the KISS principle .

However, we can proceed and see what it is going to take to complete the brightness-controller-simple install.
It is your call as to what you want to do.

1st step in making the package manager happy:
```

sudo apt install python-wxgtk3.0

```
see what the package manager relates for the next step .

With the caveat that this package and the other dependencies are not normal to a default install.  You are venturing out into deeper waters .

Again, not to break a system or make it the more difficult to maintain .

[INDENT][INDENT]we can so we do
[/INDENT][/INDENT]

---

### Post by leunam12 on 2017-12-19
Just a silly question: have you tried ```
sudo apt-get -f install
```as suggested?

---

### Post by Impavidus on 2017-12-19
Let's have a close look at that output.
> **zmckool said:**
> 
```
zack@G751JT:~$ sudo apt-get install -f
...
0 upgraded, 1 newly installed, 0 to remove and 232 not upgraded.
130 not fully installed or removed.

```
232 available upgrades is a lot, but that may be nothing more than an indication that this problem has existed for a long time. 130 partially installed packages is an awful lot and a bad thing, but if you try to install random packages just to check whether you can install them and see them fail, yes, you'll get a lot of partially installed packages. So when you've solved the root cause of your problem, your package manager will install all that stuff.
> ```

Unpacking libc6-dev-i386 (2.23-0ubuntu9) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.23-0ubuntu9_amd64.deb (--unpack):
 trying to overwrite '/usr/include/sys/uio.h', which is also in package libc6-dev-amd64:i386 2.23-0ubuntu9

```
Here we get closer to the root cause of your problem. You try to install both libc6-dev-i386 and libc6-dev-amd64:i386. Although the packages are not marked as conflicting, they do conflict, as both contain the file /usr/include/sys/uio.h. I can't make much sense of those packages. The former is the 32 bit libc6 library development files for 64 bit systems, the latter suggests to be the 32 bit version is the 64 bit libc6 library development files. I'm not sure what's supposed to be the difference.

I have neither of those packages installed on my computer. libc6-dev is sufficient for most programming. So why are these packages wanted?
> ```

The following packages have unmet dependencies:
 gcc-5-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.23-0ubuntu9) but it is not going to be installed

```
I never looked into those packages, but they appear to be for some highly specialised work:> gcc-5-multilib: This is a dependency package, depending on development packages for the non-default multilib architecture(s).

libc6-dev-x32: Contains the symlinks and object files needed to compile and link programs which use the standard C library. This is the X32 ABI version of the library, meant for amd64 systems.Are you sure you need those? If not, uninstall.

> I am trying to install this because no matter what I install I get this error.Sounds like, to demonstrate your drain is clogged you throw in some buckets of water, sand and rags. Unfortunately, that doesn't just demonstrate the problem, it makes it worse. I suggest you try to uninstall packages until your package manager is happy.

---

