---
title: "Couldn't install mplayer"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by graphicmist on 2008-11-04
one of my friends was installing some packages from the ubuntu 8.04 dvd and when he was trying to install  mplayer or vlc player from the internet using sudo apt-get command following error was coming.


```
ankit@devil:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libgif4 (>= 4.1.6) but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libxvmc1 but it is not installable
E: Broken packages


```

```
ankit@devil:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libiso9660-5 but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not going to be installed
       Depends: vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) but it is not going to be installed
       Depends: vlc-plugin-pulse but it is not going to be installed
E: Broken packages

```

what could be the problem..

---

### Post by taurus on 2008-11-04
Try

```
sudo apt-get update
sudo apt-get install mplayer
```
And if he still gets the same error message, ask him to post his /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by cloggie on 2008-11-07
Hi, 
I too have problems installing mplayer.
I get this list with all these unmet dependencies, and as far as I know, I have the right repos in my sources.

Following is the massage in my terminal window:

will@will-laptop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
           Depends: libggi2 (>= 1:2.2.2) but it is not going to be installed
           Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
           Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-2.1ubuntu1 is to be installed
           Depends: libmp3lame0 (>= 3.98) but it is not installable
           Depends: libopenal1 (>= 1:1.3.253) but it is not installable
           Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
           Depends: libspeex1 (>= 1.2~beta3-1) but 1.1.12-3ubuntu0.8.04.1 is to be installed
           Depends: libx264-59 (>= 1:0.svn20080408) but it is not installable
E: Broken packages

And the following is a listing of my repo's. maybe you can find the prob.

will@will-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse


Am I missing an important piece here maybe?

Thanks, Will.

---

### Post by cloggie on 2008-11-07
Oh shoot,

May I kick myself in the butt?
I see the problem. I have the Medibuntu repos for Intrepid installed, instead of Hardy Heron,
Sorry to have bothered you guys, sorry.
(sticks his foot in mouth)

---

