---
title: "Problems with installing libcairo2-dev"
date: 2009-12-09
forum: Repositories &amp; Backports
---

### Post by 2LSS on 2009-12-09
I am trying to install libcairo2-dev but I am getting an error message 
```
frank@frank-laptop:~$ sudo apt-get install libcairo2-dev
[sudo] password for frank: 
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
  libcairo2-dev: Depends: libcairo2 (= 1.6.0-0ubuntu2) but 1.6.0-0ubuntu3~tj~ppa2h is to be installed
E: Broken packages


```
After some searching I discovered what the problem was. A while back I added a ppa to get drivers for my webcam (thread found here, first post [http://ubuntuforums.org/archive/index.php/t-927454.html]("http://ubuntuforums.org/archive/index.php/t-927454.html")) but never removed the ppa after I got it working.
So I removed the ppa using:
```
sudo rm /etc/apt/sources.list.d/intuitivenipple.list
```
and then 
```
sudo apt-get update
```
but when trying to install libcairo2-dev I still get the same error.
Can anyone explaine to me why this is happening?

---

### Post by mgol on 2009-12-28
Try:
```
sudo aptitude reinstall libcairo2 libcairo2-dev
```

If it doesn't help, You can try to do a major cache clean first:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo apt-get update && sudo apt-get upgrade
sudo aptitude reinstall libcairo2 libcairo2-dev

```

If You are still encountering issues, please provide the output of:
```
apt-cache policy libcairo2 libcairo2-dev
```

---

### Post by 2LSS on 2009-12-28
First I tried 
```
sudo aptitude reinstall libcairo2 libcairo2-dev
```
and got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
libcairo2-dev is not currently installed, so it will not be reinstalled.
libcairo2-dev is not currently installed, so it will not be reinstalled.
The following packages are unused and will be REMOVED:
  ffmpeg gimp-help-common gimp-help-en hugin-data libcurl3 libdns35 libfame-0.9 libglib1.2ldbl libgtk1.2 libgtk1.2-common libimlib2 liblzo1 libnspr4-dev 
  libnss3-dev libopenobex1 libpano12-0 libpvm3 libswscale1d libx11-xcb1 mjpegtools obex-data-server transcode 
The following packages will be REINSTALLED:
  libcairo2 
0 packages upgraded, 0 newly installed, 1 reinstalled, 22 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 55.4MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate file for the libcairo2 package. This might mean you need to manually fix this package.
```

then I tried: (I added the -r after it complained about it being a directory)
```
sudo apt-get clean
sudo rm -r /var/lib/apt/lists/*
sudo rm -r /var/lib/apt/lists/partial/*
```

(/var/lib/apt/lists/partial/ wasn't found)
Then I updated:

```
sudo apt-get update && sudo apt-get upgrade
E: Lists directory /var/lib/apt/lists/partial is missing.
```


Because I am a dummy I didn't backup the /var/lib/apt/lists/ directory. Is there any way to replace the deleted file?

Here is the result of:
```
apt-cache policy libcairo2 libcairo2-dev
libcairo2:
  Installed: 1.6.0-0ubuntu3~tj~ppa2h
  Candidate: 1.6.0-0ubuntu3~tj~ppa2h
  Version table:
 *** 1.6.0-0ubuntu3~tj~ppa2h 0
        100 /var/lib/dpkg/status
W: Unable to locate package libcairo2-dev
```

---

### Post by mgol on 2009-12-29
> **2LSS said:**
> 
```
sudo apt-get clean
sudo rm -r /var/lib/apt/lists/*
sudo rm -r /var/lib/apt/lists/partial/*
```

(...)

Because I am a dummy I didn't backup the /var/lib/apt/lists/ directory.

You didn't have to, it should update itself after apt-get update. It seems You did invoke:
```

sudo rm -r /var/lib/apt/lists/
sudo rm -r /var/lib/apt/lists/partial/

```
instead of:
```

sudo rm -r /var/lib/apt/lists/*
sudo rm -r /var/lib/apt/lists/partial/*

```
am I right?

**(EDIT: The "-r" parameter was the source of "partial" directory removal, not what I wrote above, my mistake)**

Then You deleted directories and I was talking only about their contents. Recreate them and try to update again:
```

sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update && sudo apt-get upgrade.

```

> **2LSS said:**
> 
```
apt-cache policy libcairo2 libcairo2-dev
libcairo2:
  Installed: 1.6.0-0ubuntu3~tj~ppa2h
  Candidate: 1.6.0-0ubuntu3~tj~ppa2h
  Version table:
 *** 1.6.0-0ubuntu3~tj~ppa2h 0
        100 /var/lib/dpkg/status
W: Unable to locate package libcairo2-dev
```
Wow. libcairo2 is in default repositories, You have to have it unless You deleted default repos which shouldn't be ever done. I need some additional info:
```

lsb_release -a
cat /etc/apt/sources.list
ls -lA /etc/apt/sources.list.d/
for repo_file in /etc/apt/sources.list.d/*; do echo " *** $repo_file *** "; cat "$repo_file"; echo; done

```

---

### Post by 2LSS on 2009-12-29
Here is the log of what I did:
```
frank@frank-laptop:~$ sudo rm /var/lib/apt/lists/*
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
frank@frank-laptop:~$ sudo rm -r /var/lib/apt/lists/*
frank@frank-laptop:~$ sudo rm /var/lib/apt/lists/partial/*
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
frank@frank-laptop:~$ sudo rm -r /var/lib/apt/lists/partial/*
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
```

After making the directory 'partial' I was able to update and upgrade.
Then I retried:
```
frank@frank-laptop:~$ apt-cache policy libcairo2 libcairo2-dev
libcairo2:
  Installed: 1.6.0-0ubuntu3~tj~ppa2h
  Candidate: 1.6.0-0ubuntu3~tj~ppa2h
  Version table:
 *** 1.6.0-0ubuntu3~tj~ppa2h 0
        100 /var/lib/dpkg/status
     1.6.0-0ubuntu2 0
        500 http://mirror.anl.gov hardy-updates/main Packages
     1.6.0-0ubuntu1 0
        500 http://mirror.anl.gov hardy/main Packages
libcairo2-dev:
  Installed: (none)
  Candidate: 1.6.0-0ubuntu2
  Version table:
     1.6.0-0ubuntu2 0
        500 http://mirror.anl.gov hardy-updates/main Packages
     1.6.0-0ubuntu1 0
        500 http://mirror.anl.gov hardy/main Packages
```

Then I tried reinstalling libcairo2 but got the same error:
```
E: I wasn't able to locate file for the libcairo2 package. This might mean you need to manually fix this package.
```

Here is:
```
frank@frank-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.3 LTS
Release:	8.04
Codename:	hardy
```

```
frank@frank-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.anl.gov/pub/ubuntu/ hardy main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirror.anl.gov/pub/ubuntu/ hardy universe
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy universe
deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ hardy multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy multiverse
deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://mirror.anl.gov/pub/ubuntu/ hardy-security main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-security main restricted
deb http://mirror.anl.gov/pub/ubuntu/ hardy-security universe
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-security universe
deb http://mirror.anl.gov/pub/ubuntu/ hardy-security multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-security multiverse
# deb http://directhex.mfgames.com/ hardy main
deb http://www.linuxcnc.org/hardy hardy base emc2.2
deb-src http://www.linuxcnc.org/hardy hardy base emc2.2
deb http://ppa.launchpad.net/transmissionbt/ubuntu hardy main
deb-src http://ppa.launchpad.net/transmissionbt/ubuntu hardy main
deb http://www.tolaris.com/apt/ hardy main

deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu hardy main
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main
deb http://getswiftfox.com/builds/debian unstable non-free
```

```
frank@frank-laptop:~$ ls -lA /etc/apt/sources.list.d/
total 52
-rw-r--r-- 1 root root  48 2009-12-07 01:44 google-chrome.list
-rw-r--r-- 1 root root  48 2009-12-07 01:44 google-chrome.list.save
-rw-r--r-- 1 root root 277 2009-12-07 01:44 medibuntu.list
-rw-r--r-- 1 root root 277 2009-09-03 15:05 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 277 2009-12-07 01:44 medibuntu.list.save
-rw-r--r-- 1 root root 353 2009-12-07 01:44 opera.list
-rw-r--r-- 1 root root 353 2009-12-07 01:44 opera.list.save
-rw-r--r-- 1 root root 176 2009-12-07 01:44 playonlinux.list
-rw-r--r-- 1 root root 176 2009-09-03 15:05 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root 176 2009-12-07 01:44 playonlinux.list.save
-rw-r--r-- 1 root root 181 2009-12-07 01:44 winehq.list
-rw-r--r-- 1 root root 181 2009-09-03 15:05 winehq.list.distUpgrade
-rw-r--r-- 1 root root 181 2009-12-07 01:44 winehq.list.save
```

When I tried 
```
do echo " *** $repo_file *** "; cat "$repo_file"; echo; done
```
I got some syntax errors. It didn't like the ; between echo and done. Did you want this instead?
```
echo " *** $repo_file *** ";cat "$repo_file"; echo done

```

---

### Post by mgol on 2009-12-29
> **2LSS said:**
> Here is the log of what I did:
(...)

I didn't provide "-r" parameter not by mistake - an error to remove partial directory is normal and desired - I didn't want it to be deleted; You shouldn't add "-r", but - fortunately - it was enough to recreate the directory.

> **2LSS said:**
> 
When I tried 
```
do echo " *** $repo_file *** "; cat "$repo_file"; echo; done
```
I got some syntax errors. It didn't like the ; between echo and done. Did you want this instead?
```
echo " *** $repo_file *** ";cat "$repo_file"; echo done

```
No, it was correct, echo without parameters just prints an empty line, it's not important; but I meant the whole loop, started with 'for':
```
for repo_file in /etc/apt/sources.list.d/*; do echo " *** $repo_file *** "; cat "$repo_file"; echo; done
```

But it's not important; You just have a newer version of a package, You have to downgrade it; try this:
```
sudo apt-get purge libcairo2
sudo apt-get install libcairo2 libcairo2-dev

```

Everything should be fine after that.

---

### Post by 2LSS on 2009-12-29
I'm a little confused
when I try 
sudo apt-get purge libcairo2
sudo apt-get autoremove libcairo2
sudo apt-get remove libcairo2

they all want to remove every package that depends on libcairo2 (brasero, cheese, evolution, etc)

Is there a way around this?

---

### Post by mgol on 2009-12-29
> **2LSS said:**
> 
they all want to remove every package that depends on libcairo2 (brasero, cheese, evolution, etc)

Right, too many packages depends on this, so it won't go so easy. :) Try this command:
```
sudo aptitude install libcairo2=1.6.0-0ubuntu2
```

---

### Post by 2LSS on 2009-12-29
Ok that worked! libcario2-dev installed ok as well. 

```
libcairo2:
  Installed: 1.6.0-0ubuntu2
  Candidate: 1.6.0-0ubuntu2
  Version table:
 *** 1.6.0-0ubuntu2 0
        500 http://mirror.anl.gov hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1.6.0-0ubuntu1 0
        500 http://mirror.anl.gov hardy/main Packages
libcairo2-dev:
  Installed: 1.6.0-0ubuntu2
  Candidate: 1.6.0-0ubuntu2
  Version table:
 *** 1.6.0-0ubuntu2 0
        500 http://mirror.anl.gov hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1.6.0-0ubuntu1 0
        500 http://mirror.anl.gov hardy/main Packages
```


dzi&#281;kuj&#281;!  (hopefully that means thank you :))

---

### Post by mgol on 2009-12-29
> **2LSS said:**
> 
dzi&#281;kuj&#281;!  (hopefully that means thank you :))
That's right. Nice to hear a domestic word here. :)

---

