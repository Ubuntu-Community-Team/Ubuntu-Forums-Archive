---
title: "How do I install subversion"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by degarb on 2011-12-27
I have ubu 9.10 and upgrade fails, not enough space.  And I it took 2 days to install wireless card with no ethernet.  I cannot afford a day of downtime on machine.

when I tpye sudo apt-get install subversion  I just get unable to fetch file error.

---

### Post by oldos2er on 2011-12-27
Since 9.10 is no longer supported, its repositories are no longer being updated and have moved to "old releases". [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by degarb on 2011-12-27
> **oldos2er said:**
> Since 9.10 is no longer supported, its repositories are no longer being updated and have moved to "old releases". [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)


This tells me nothing I do not know.  Unless I am missing something. I explained upgrading is not an option.   

Can svn be installed from cd or do i ADD Somthing to the repo that will allow the ubuntu community to not kill my machine?

---

### Post by oldos2er on 2011-12-27
Rudeness is unnecessary. I have no way of knowing what you know or don't know if you don't post it. 

I'll assume then you've already changed your /etc/apt/sources.list file to the old-releases repositories, run ```
sudo apt-get update && sudo apt-get install subversion
``` If you still have errors please post the full terminal output of the above command.

---

### Post by degarb on 2011-12-27
> **oldos2er said:**
> Rudeness is unnecessary. I have no way of knowing what you know or don't know if you don't post it. 

I'll assume then you've already changed your /etc/apt/sources.list file to the old-releases repositories, run ```
sudo apt-get update && sudo apt-get install subversion
``` If you still have errors please post the full terminal output of the above command.


I was frustrated, but didn't think I was rude.  If so, I apologize.  I just think that the state of learning and teaching could be improved by one rule: never obfuscate, never give irrelevant info, and don't state the obvious.  However, it is not obvious, what the "obvious" obviously is.  So obviously, that can be excused, if not obviated.

Now, I am pretty sure I have not "changed my /etc/apt/sources.list" to old release repo"   Where do I get this list?

output: Unable to fetch file, server said 'Failed to open file.  '
Fetched 308B in 39s (8B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FE8956A73C5EE1C9
W: Failed to fetch [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/main/source/Sources.gz](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/main/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/restricted/source/Sources.gz](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/restricted/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/main/binary-i386/Packages.gz](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/multiverse/binary-i386/Packages.gz](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/multiverse/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/restricted/binary-i386/Packages.gz](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/restricted/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/multiverse/source/Sources.gz](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/multiverse/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/universe/source/Sources.gz](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/universe/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/universe/binary-i386/Packages.gz](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/dists/karmic/universe/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by degarb on 2011-12-27
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/) karmic main multiverse restricted
deb-src [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/) karmic main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [ftp://ftp.egr.msu.edu/pub/ubuntu/archive/](ftp://ftp.egr.msu.edu/pub/ubuntu/archive/) karmic universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb apps
deb-src [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb apps
deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) gutsy main
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main

deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) jaunty main

deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

---

### Post by degarb on 2011-12-28
After googling for a few hours(no hints here.) I added/changed to: 

```
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse 


but only getting $ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate
  
after apt get udate
```

---

### Post by Old_Grey_Wolf on 2011-12-28
Use gedit to edit your sources.list file. Enter this in a terminal 
```
gksudo gedit /etc/apt/sources.list
```

when the file opens use find and replace to replace all occurrences of "http://us.archive.ubuntu.com/ubuntu/ karmic" with "http://old-releases.ubuntu.com/ubuntu/ karmic".

Save the file.

Then do ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install subversion

```

When Ubuntu 12.04 is released at the end of April I would recommend you install that version. It will be supported for 5 years.

---

### Post by degarb on 2011-12-28
> **Old_Gray_Wolf said:**
> 

when the file opens use find and replace to replace all occurrences of "http://us.archive.ubuntu.com/ubuntu/ karmic" with "http://old-releases.ubuntu.com/ubuntu/ karmic".

Save the file.

Then do ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install subversion

```

When Ubuntu 12.04 is released at the end of April I would recommend you install that version. It will be supported for 5 years.


This "replace all: is the missing link, with the repos I needed, I have been looking for all my life!  Well, a bit of exaggeration, I guess--but really worked!  Thanks.

I held off on the apt-get upgrade, since in the past it complained not enough space with over 200 megs free.  I am guessing any upgrade will quickly eat up any free space with only dubious security patches. With browser cache and music listening, I dropped from 200 megs a few days ago to about 30 megs free today.  I did sudo apt get clean.  I ran janitor.  I  think pinguy uses a better clean up program, but don't recall the name.

---

### Post by dFlyer on 2011-12-28
another place you can free up some space is by deleting some old backup logs in /var/log

---

### Post by degarb on 2011-12-28
Crap!   At first, I was able to install one deb, that had python dependencies.  It worked. Then I noticed synaptic and other things wouldn't launch unless, I sudo launched via terminal.  complaining some certificate could not be copied.

Then, I rebooted, now it refused to log in.   

So, what do I do?

This is a 6 gig drive that had like 600 megs free after initial 9.10 install.  But got browsing, music, video, office to work.   I am assuming 11 would be too large for drive since 9.1 barely fit on machine.

---

### Post by snowpine on 2011-12-28
15gb is the recommended minimum hard drive space for Ubuntu. I recommend a new hard drive (there are some great after-holiday sales going on right now) and a fresh install of a supported Ubuntu release (10.04 or newer).

---

### Post by degarb on 2011-12-28
Update: I was able to log in as root.  It is telling me there is 0bytes left; but when I open disk usage analyzer I see 235 megs free on disk; but when I open computer, I see 0 bytes free on filesystem.

I don't understand.

---

### Post by degarb on 2011-12-28
Okay, I--logged in as root since user would not login-- found bleach bit used it, deleteded everything in home, uninstalled firefox.  Now it is showing anything from 15 megs free to 350 megs free depeding what directory in computer I am in.

But I was forced to change the user name.  Now I can get into the user account, however the wireless card is lit up, but no wireless icon at top!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!   This computer is worthless without wireless (no ethernet port). I went to  network and made sure the sid is there with proper security code.  How do I get the wireless back?  It is obviously getting juice just not proper software to run it.

---

### Post by degarb on 2011-12-28
it appears the old network applet uses old password to run, so had to reboot and enter old password.  Weird.

How do you launch this applet when needed?  Without this applet wireless is apparently useless.

---

### Post by degarb on 2011-12-28
> **snowpine said:**
> 15gb is the recommended minimum hard drive space for Ubuntu. I recommend a new hard drive (there are some great after-holiday sales going on right now) and a fresh install of a supported Ubuntu release (10.04 or newer).

I guess, since I got machine running I will respond to this.  Apart from being costly.  I could pick up two more 600mhz 6 gig drive laptop machines for $35 each.  I have been holding off, because of distro bloat.  It appears that getting these machine to live may be impossible with the size creep in just 2 years.  At this rate, you will need a 60 gig drive in two years to get the 2014 version to run.  xp, on this machine, ran in a 6 gig virtual machine.  ( I connected a 10 gig external to the machine and ran under ubuntu.  It ran fine. Problem is that this is the educational family living room machine that lives beside and connects to entertainment center; wife ripped off the ugly external drive (and troublesome usb jump drive) and threw it away/some place I have no idea.  I am lucky the audio rca cord remains.)

---

### Post by Old_Grey_Wolf on 2011-12-28
If you want to keep those old machines working, maybe you should look into one of these alternatives...[http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/](http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/) or possibly these [http://bloggerspath.com/5-best-lightweight-linux-distributions-your-old-computers/](http://bloggerspath.com/5-best-lightweight-linux-distributions-your-old-computers/)

---

