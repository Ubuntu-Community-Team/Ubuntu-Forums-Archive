---
title: "how to install GCC?"
date: 2007-05-07
forum: Programming Talk
---

### Post by adameye on 2007-05-07
I just downloaded Ubuntu 7.04 and installed it
however, I can not use gcc,cc,g++ to compile the C program which can run in Ubuntu 6.10

[COLOR="Red"]sudo aptitude update[/COLOR]
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release [34.7kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [38.4kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [44.6kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources [274kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources [1436B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1068kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [81.1kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [24.2kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [17.8kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [40.1kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [6087B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources [5571B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources [14B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources [14.4kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources [2382B]
Fetched 6158kB in 2m3s (49.8kB/s)
Reading package lists... Done

[COLOR="Red"]sudo aptitude install build-essential[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
g++-4.1 libc6-dev libstdc++6-4.1-dev
The following NEW packages will be automatically installed:
dpkg-dev g++ linux-libc-dev
The following NEW packages will be installed:
build-essential dpkg-dev g++ linux-libc-dev
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7932kB of archives. After unpacking 30.4MB will be used.
The following packages have unmet dependencies:
g++-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
Depends: gcc-4.1 (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
libstdc++6-4.1-dev: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
libc6-dev: Depends: libc6 (= 2.4-1ubuntu12.3) but 2.5-0ubuntu14 is installed.
Resolving dependencies...
open: 9; closed: 5; defer: 0; conflict/break: 1 .The following actions will resolve these dependencies:

Keep the following packages at their current version:
build-essential [Not Installed]
g++ [Not Installed]
g++-4.1 [Not Installed]
libc6-dev [Not Installed]
libstdc++6-4.1-dev [Not Installed]

Score is -9965

Accept this solution? [Y/n/q/?]

---

### Post by WW on 2007-05-07
You say you installed 7.04 (feisty), but all the repositories printed by 'sudo aptitude update'  are edgy.  I suspect you did not upgrade correctly, or you have somehow created an incorrect /etc/apt/sources.list.

---

### Post by adameye on 2007-05-07
thanks, I found [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

so this should be the right source list for 7.04, right?
(I think the orignal source list of 7.04 is "edgy", let me check later(when I go home today)

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

---

### Post by taurus on 2007-05-07
Or here is another one.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 

```

---

### Post by adameye on 2007-05-07
yes, it works, thank you very much!

---

