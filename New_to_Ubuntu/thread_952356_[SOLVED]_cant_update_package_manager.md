---
title: "[SOLVED] cant update package manager"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by bjhome on 2008-10-19
'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


I have this error can anybody give me step by step instructions Please.?

---

### Post by bjhome on 2008-10-19
dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
bev@bev-laptop:~$

---

### Post by Elfy on 2008-10-19
There appear to be a lot of these errors - can you post sources list please

```
cat /etc/apt/sources.list
```

---

### Post by bjhome on 2008-10-19
cat /etc/apt/sources.listbev@bev-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy main
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates main
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END
bev@bev-laptop:~$

---

### Post by Elfy on 2008-10-19
Start with editing the sources list, backup first - comment out all of the Ultimatxi repos, they're not needed and can cause problems. It's a rehash apprently of Automatix which used to cause problems. [http://www.qense.nl/posts/ubuntu-nl-warns-for-ultimatix](http://www.qense.nl/posts/ubuntu-nl-warns-for-ultimatix)

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.1910
gksudo gedit /etc/apt/sources.list
```

Put a # at the beginning of the lines under #ULTAMATIX REPOS START, then save and close, now run an update

```
sudo apt-get update
```

---

### Post by Ryadt on 2008-10-19
Replace these> 
deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all by ```
deb http://repoubuntusoftware.info hardy all
```

---

### Post by bjhome on 2008-10-19
How do i backup ? do i just run these to codes that you have given me?

---

### Post by Elfy on 2008-10-19
Yes - the first command copies the file from /etc/apt/sources.list to  /etc/apt/sources.list.1910

The second opens the file to edit it

---

### Post by bjhome on 2008-10-19
Do i have to put everything on a disc first?

---

### Post by Elfy on 2008-10-19
> **Ryadt said:**
> Replace these by ```
deb http://repoubuntusoftware.info hardy all
```

Personally I wouldn't do that - why trust a 'company' which can't even get their repository address correct and then cause people problems, further I don't see anything available there that isn't already available.

But that of course is just my opinion.

---

### Post by Elfy on 2008-10-19
> **bjhome said:**
> Do i have to put everything on a disc first?

? Not sure what you mean.

---

### Post by bjhome on 2008-10-19
I have run the first one and put # in front of the repo ones now do i just close it. then run the other one?

---

### Post by Elfy on 2008-10-19
save and close then run the update command

---

### Post by bjhome on 2008-10-19
looks like I'm all good to go. thanks forestpixie :

---

### Post by Elfy on 2008-10-19
You're welcome - can you mark the thread solved please - thread tools at top of page :)

---

