---
title: "Bluefish &amp; gftp?"
date: 2005-02-18
forum: Repositories &amp; Backports
---

### Post by ions on 2005-02-18
I can't install either of them.

```
 $ sudo apt-get install bluefish
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bluefish: Depends: libpcre3 (>= 4.5) but it is not installable
E: Broken packages

```

```
$ sudo apt-get install gftp
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.17-6) but it is not installable
        Depends: gftp-text (= 2.0.17-6) but it is not going to be installed
E: Broken packages

```

This is my sources.list:

```
## The following are from http://ubuntuguide.org/#extrarepositories

deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe

```

Is there an easy way to figure out what is where?  In portage I could do an emerge -s foo and 99.9% of the time it would find foo.

---

### Post by Yukonjack on 2005-02-18
Add these to your sources.list

```
deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted
```

It replace deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe you can get rid of that one.

---

### Post by ions on 2005-02-18
I addded those 2 repositories and took out the 'bp' one.  Tried to emerge Bluefish and got the identical error.  Same with gftp.  :(

---

### Post by ions on 2005-02-18
xmms fails as well...

```
$ sudo apt-get install xmms
Reading Package Lists... Done
Building Dependency Tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate
```

---

### Post by Yukonjack on 2005-02-18
Did you update the list before trying installing?
Everything works good for me don't know what your problem might be, try using Synaptic see if makes a difference.

---

### Post by WW on 2005-02-18
As Yukonjack suggested, you probably need to update first.  Whenever you change your repository list (or whenever you think the repositories themselves might have new packages), you should either run```
sudo apt-get update
``` or run Synaptic and hit the Reload button.

---

### Post by ions on 2005-02-18
```
$ sudo apt-get update
Password:
Get:1 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/main Packages [13.2kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [102B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [108B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [104B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [110B]
Get:6 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/main Release [93B]
Get:7 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/universe Packages [29.2kB]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Release
Get:8 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/universe Release [97B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Get:9 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/multiverse Packages [20B]
Get:10 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/multiverse Release [99B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
Get:11 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/restricted Packages [20B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Get:12 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/restricted Release [99B]
Get:13 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/main Packages [20B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Release
Get:14 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/main Release [90B]
Get:15 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/universe Packages [2388B]
Get:16 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/universe Release [94B]
Get:17 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/multiverse Packages [20B]
Get:18 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/multiverse Release [96B]
Get:19 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/restricted Packages [20B]
Get:20 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/restricted Release [96B]
Fetched 46.1kB in 3s (13.2kB/s)
Reading Package Lists... Done
chris@tux:~ $ sudo apt-get install xmms
Reading Package Lists... Done
Building Dependency Tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

```

Bluefish and gftp also remain with the same error.

---

### Post by ions on 2005-02-18
This is my sources.list in full:

```
##deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


#deb http://archive.ubuntu.com/ubuntu warty main restricted
#deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu warty universe
# deb-src http://archive.ubuntu.com/ubuntu warty universe

#deb http://security.ubuntu.com/ubuntu warty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu warty-security main restricted

## The following are from http://ubuntuguide.org/#extrarepositories

deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted

```

---

### Post by ions on 2005-02-18
I hit reload in Synaptic and the errors remain.

---

### Post by Yukonjack on 2005-02-18
[QUOTE=ions]This is my sources.list in full:

```
##deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


#deb http://archive.ubuntu.com/ubuntu warty main restricted
#deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu warty universe
# deb-src http://archive.ubuntu.com/ubuntu warty universe

#deb http://security.ubuntu.com/ubuntu warty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu warty-security main restricted

## The following are from http://ubuntuguide.org/#extrarepositories

deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted

```[/QUOTE]


I see your problem now you have to activate some of the respository, follow mine and it will work 
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted

```

---

### Post by ions on 2005-02-18
[QUOTE=Yukonjack]I see your problem now you have to activate some of the respository, follow mine and it will work 
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted

```[/QUOTE]
 Spiffy!  Thank you!  :)

---

### Post by Yukonjack on 2005-02-18
Your welcome, glad to help  :D

---

### Post by neighborlee on 2005-02-23
[QUOTE=Yukonjack]I see your problem now you have to activate some of the respository, follow mine and it will work 
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted

```[/QUOTE]

-----------
hi guys.

   I desperately need an extra pair of eyes I think today..I've checked my sources.list file and added multiverse and still gftp wont install and here is my sources.list file and the error I"m getting:::
-----------------------

sources.list:
========
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted   

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe   

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted   
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse


gftp install error:
===========
gftp:
  Depends: gftp-gtk but 2.0.17-6ubuntu0.2 is to be installed
 Depends: gftp-text but it is not going to be installed

and yes I updated before trying it..

thx anyone
nl

---

### Post by Yukonjack on 2005-02-23
Hi NL

Add these to your sources.list and it should work 

```
deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted
```

---

### Post by neighborlee on 2005-02-23
[QUOTE=Yukonjack]Hi NL

Add these to your sources.list and it should work 

```
deb http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted
```[/QUOTE]
------
crud since when I thought I was being so clever LOL..yeah indeed I forgot to see the backport line in one of the posts in here ..damn

Im curious though..why is gftp in backports ..I mean ubuntu is unstable branch afterall right ? ;-)

thx ;-))
nl
'eyes wide open'

---

