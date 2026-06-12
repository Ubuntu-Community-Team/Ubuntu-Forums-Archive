---
title: "gzip error w/ apt-get update"
date: 2006-02-12
forum: Repositories &amp; Backports
---

### Post by kevdep on 2006-02-12
Alright, I'm a newbie to Ubuntu/Linux and this is my first post on the forums so hopefully I'm doing this correctly.

The problem I'm having is that when I do an apt-get update I always get the same error about gzip ( I assume gzip is a zip extractor).  It always comes up when it tries to get universe packages from security.ubunutu.com and, as far as I remember, not for anything else.  I've tried different source lists, but they all seem to return the same error, although I believe they all had the same security.ubuntu.com line in them.  The ironic part about this is the second to last line that is printed when I do apt-get update: "You may want to run apt-get update to correct these problems".  WHAT???

Does anyone have a solution?  This seems to be a fairly fundamental problem because when I try doing other types of installs, they all return errors refering to the security.ubuntu.com repo. Here's what I get: 


kevin@ubuntu:~$ sudo apt-get update
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Get:1 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages [545B]
Get:2 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages [2337B]
Get:3 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources [316B]
Get:4 [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources [473B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [1560B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources [380B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [30.9kB]
99% [8 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.182)]                                         3259B/s 0s
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Sub-process gzip returned an error code (1)
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 5616B in 48s (116B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


And here's my current sources list (which i got from here):

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
## deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
## deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## opera web browser
## deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

---

### Post by bernardfrancois on 2006-02-12
Did you try **apt-get dist-upgrade**? That can also solve some apt-get problems.

Note:
- You can also use **synaptic** as a graphical front-end for apt-get.
- If you want to know what gzip is, type **man gzip** in the command-line, or type **whatis gzip** for a short description.

---

### Post by kevdep on 2006-02-12
Thanks for the reply.  I tried the dist-upgrade and got this:

```
kevin@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
```

I did try simply commenting out the all of the security.ubuntu lines in my sources list, which made the apt-get update function work without any errors, but I'm not sure if this is ok.  Do you need to have the security repos enabled?

---

### Post by mmcmonster on 2006-02-14
I have pretty much the same problem:
```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

Maybe something happened to the repository in the last couple weeks?  Things were definitely working correctly about a month ago.

As another bit of information, my ISP is Service Electric Cable in Pennsylvania.

EDIT:
Never mind.  My problem was solved by following the instructions in the following post:

[http://www.ubuntuforums.org/showpost.php?p=727056&postcount=9](http://www.ubuntuforums.org/showpost.php?p=727056&postcount=9)

---

### Post by kevdep on 2006-02-16
Thanks for the post, I ended up reinstalling Ubuntu before you posted (its what a native windows user does), and all's fine.  Oh well, I wanted to increase the size of the partition it was on anyway.

---

### Post by bernardfrancois on 2006-02-18
It's possible to change the size of a partition without having to format it or to loose any data. I dunno how to do this in LInux (probably there's a command-line tool, or maybe with gparted), but since I have a dual boot system I always used partition magic (which works fine for me but is not for free).

---

