---
title: "update problem"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by pardesi on 2008-10-22
i modified the sources.list file to direct it to my institute server which is the official server of ubuntu in india.
after that i am getting this when i do
```
sudo apt-get update
```
```

pardesi@pardesi:~$ sudo apt-get update
Hit ftp://10.65.0.42 hardy Release.gpg
Get:1 ftp://10.65.0.42 hardy/main Translation-en_IN
Ign ftp://10.65.0.42 hardy/main Translation-en_IN
Get:2 ftp://10.65.0.42 hardy/restricted Translation-en_IN
Ign ftp://10.65.0.42 hardy/restricted Translation-en_IN
Get:3 ftp://10.65.0.42 hardy/universe Translation-en_IN
Ign ftp://10.65.0.42 hardy/universe Translation-en_IN
Get:4 ftp://10.65.0.42 hardy/multiverse Translation-en_IN
Ign ftp://10.65.0.42 hardy/multiverse Translation-en_IN
Get:5 ftp://10.65.0.42 hardy/partner Translation-en_IN
Ign ftp://10.65.0.42 hardy/partner Translation-en_IN
Hit ftp://10.65.0.42 hardy-updates Release.gpg
Get:6 ftp://10.65.0.42 hardy-updates/main Translation-en_IN
Ign ftp://10.65.0.42 hardy-updates/main Translation-en_IN
Get:7 ftp://10.65.0.42 hardy-updates/restricted Translation-en_IN
Ign ftp://10.65.0.42 hardy-updates/restricted Translation-en_IN
Get:8 ftp://10.65.0.42 hardy-updates/universe Translation-en_IN
Ign ftp://10.65.0.42 hardy-updates/universe Translation-en_IN
Get:9 ftp://10.65.0.42 hardy-updates/multiverse Translation-en_IN
Ign ftp://10.65.0.42 hardy-updates/multiverse Translation-en_IN
Get:10 ftp://10.65.0.42 hardy-backports Release.gpg [189B]
Get:11 ftp://10.65.0.42 hardy-backports/main Translation-en_IN
Ign ftp://10.65.0.42 hardy-backports/main Translation-en_IN
Get:12 ftp://10.65.0.42 hardy-backports/restricted Translation-en_IN
Ign ftp://10.65.0.42 hardy-backports/restricted Translation-en_IN
Get:13 ftp://10.65.0.42 hardy-backports/universe Translation-en_IN
Ign ftp://10.65.0.42 hardy-backports/universe Translation-en_IN
Get:14 ftp://10.65.0.42 hardy-backports/multiverse Translation-en_IN
Ign ftp://10.65.0.42 hardy-backports/multiverse Translation-en_IN
Hit ftp://10.65.0.42 hardy-security Release.gpg
Get:15 ftp://10.65.0.42 hardy-security/main Translation-en_IN
Ign ftp://10.65.0.42 hardy-security/main Translation-en_IN
Get:16 ftp://10.65.0.42 hardy-security/restricted Translation-en_IN
Ign ftp://10.65.0.42 hardy-security/restricted Translation-en_IN
Get:17 ftp://10.65.0.42 hardy-security/universe Translation-en_IN
Ign ftp://10.65.0.42 hardy-security/universe Translation-en_IN
Get:18 ftp://10.65.0.42 hardy-security/multiverse Translation-en_IN
Ign ftp://10.65.0.42 hardy-security/multiverse Translation-en_IN
Hit ftp://10.65.0.42 hardy Release
Hit ftp://10.65.0.42 hardy-updates Release
Get:19 ftp://10.65.0.42 hardy-backports Release [44.0kB]
Hit ftp://10.65.0.42 hardy-security Release
Hit ftp://10.65.0.42 hardy/main Packages
Hit ftp://10.65.0.42 hardy/restricted Packages
Get:20 ftp://10.65.0.42 hardy/main Sources
Ign ftp://10.65.0.42 hardy/main Sources
Get:21 ftp://10.65.0.42 hardy/restricted Sources
Ign ftp://10.65.0.42 hardy/restricted Sources
Hit ftp://10.65.0.42 hardy/universe Packages
Get:22 ftp://10.65.0.42 hardy/universe Sources
Ign ftp://10.65.0.42 hardy/universe Sources
Hit ftp://10.65.0.42 hardy/multiverse Packages
Get:23 ftp://10.65.0.42 hardy/multiverse Sources
Ign ftp://10.65.0.42 hardy/multiverse Sources
Hit ftp://10.65.0.42 hardy-updates/main Packages
Hit ftp://10.65.0.42 hardy-updates/restricted Packages
Get:24 ftp://10.65.0.42 hardy-updates/main Sources
Ign ftp://10.65.0.42 hardy-updates/main Sources
Get:25 ftp://10.65.0.42 hardy-updates/restricted Sources
Ign ftp://10.65.0.42 hardy-updates/restricted Sources
Hit ftp://10.65.0.42 hardy-updates/universe Packages
Get:26 ftp://10.65.0.42 hardy-updates/universe Sources
Ign ftp://10.65.0.42 hardy-updates/universe Sources
Hit ftp://10.65.0.42 hardy-updates/multiverse Packages
Get:27 ftp://10.65.0.42 hardy-updates/multiverse Sources
Ign ftp://10.65.0.42 hardy-updates/multiverse Sources
Get:28 ftp://10.65.0.42 hardy-backports/main Packages [108kB]
Get:29 ftp://10.65.0.42 hardy-backports/restricted Packages [14B]
Get:30 ftp://10.65.0.42 hardy-backports/universe Packages [81.3kB]
Get:31 ftp://10.65.0.42 hardy-backports/multiverse Packages [13.9kB]
Get:32 ftp://10.65.0.42 hardy-backports/main Sources  
Ign ftp://10.65.0.42 hardy-backports/main Sources
Get:33 ftp://10.65.0.42 hardy-backports/restricted Sources
Ign ftp://10.65.0.42 hardy-backports/restricted Sources
Get:34 ftp://10.65.0.42 hardy-backports/universe Sources
Ign ftp://10.65.0.42 hardy-backports/universe Sources
Get:35 ftp://10.65.0.42 hardy-backports/multiverse Sources
Ign ftp://10.65.0.42 hardy-backports/multiverse Sources
Hit ftp://10.65.0.42 hardy-security/main Packages
Hit ftp://10.65.0.42 hardy-security/restricted Packages
Get:36 ftp://10.65.0.42 hardy-security/main Sources
Ign ftp://10.65.0.42 hardy-security/main Sources
Get:37 ftp://10.65.0.42 hardy-security/restricted Sources
Ign ftp://10.65.0.42 hardy-security/restricted Sources
Hit ftp://10.65.0.42 hardy-security/universe Packages
Get:38 ftp://10.65.0.42 hardy-security/universe Sources
Ign ftp://10.65.0.42 hardy-security/universe Sources
Hit ftp://10.65.0.42 hardy-security/multiverse Packages
Get:39 ftp://10.65.0.42 hardy-security/multiverse Sources
Ign ftp://10.65.0.42 hardy-security/multiverse Sources
Get:40 ftp://10.65.0.42 hardy/main Sources
Err ftp://10.65.0.42 hardy/main Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:41 ftp://10.65.0.42 hardy/restricted Sources
Err ftp://10.65.0.42 hardy/restricted Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:42 ftp://10.65.0.42 hardy/universe Sources
Err ftp://10.65.0.42 hardy/universe Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:43 ftp://10.65.0.42 hardy/multiverse Sources
Err ftp://10.65.0.42 hardy/multiverse Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:44 ftp://10.65.0.42 hardy-updates/main Sources
Err ftp://10.65.0.42 hardy-updates/main Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:45 ftp://10.65.0.42 hardy-updates/restricted Sources
Err ftp://10.65.0.42 hardy-updates/restricted Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:46 ftp://10.65.0.42 hardy-updates/universe Sources
Err ftp://10.65.0.42 hardy-updates/universe Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:47 ftp://10.65.0.42 hardy-updates/multiverse Sources
Err ftp://10.65.0.42 hardy-updates/multiverse Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:48 ftp://10.65.0.42 hardy-backports/main Sources
Err ftp://10.65.0.42 hardy-backports/main Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:49 ftp://10.65.0.42 hardy-backports/restricted Sources
Err ftp://10.65.0.42 hardy-backports/restricted Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:50 ftp://10.65.0.42 hardy-backports/universe Sources
Err ftp://10.65.0.42 hardy-backports/universe Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:51 ftp://10.65.0.42 hardy-backports/multiverse Sources
Err ftp://10.65.0.42 hardy-backports/multiverse Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:52 ftp://10.65.0.42 hardy-security/main Sources
Err ftp://10.65.0.42 hardy-security/main Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:53 ftp://10.65.0.42 hardy-security/restricted Sources
Err ftp://10.65.0.42 hardy-security/restricted Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:54 ftp://10.65.0.42 hardy-security/universe Sources
Err ftp://10.65.0.42 hardy-security/universe Sources
  Unable to fetch file, server said 'Failed to open file.  '
Get:55 ftp://10.65.0.42 hardy-security/multiverse Sources
Err ftp://10.65.0.42 hardy-security/multiverse Sources
  Unable to fetch file, server said 'Failed to open file.  '
Fetched 248kB in 1s (160kB/s)
W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy/main/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy/restricted/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy/universe/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy/multiverse/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-updates/main/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-updates/universe/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-backports/main/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-backports/restricted/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-backports/universe/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-security/main/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-security/restricted/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-security/universe/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch ftp://10.65.0.42/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  Unable to fetch file, server said 'Failed to open file.  '

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Here is my sources.list file
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb ftp://10.65.0.42/ubuntu/ hardy main restricted
deb-src ftp://10.65.0.42/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb ftp://10.65.0.42/ubuntu/ hardy-updates main restricted
deb-src ftp://10.65.0.42/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb ftp://10.65.0.42/ubuntu/ hardy universe
deb-src ftp://10.65.0.42/ubuntu/ hardy universe
deb ftp://10.65.0.42/ubuntu/ hardy-updates universe
deb-src ftp://10.65.0.42/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb ftp://10.65.0.42/ubuntu/ hardy multiverse
deb-src ftp://10.65.0.42/ubuntu/ hardy multiverse
deb ftp://10.65.0.42/ubuntu/ hardy-updates multiverse
deb-src ftp://10.65.0.42/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb ftp://10.65.0.42/ubuntu/ hardy-backports main restricted universe multiverse
deb-src ftp://10.65.0.42/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb ftp://10.65.0.42/ubuntu hardy partner
deb-src ftp://10.65.0.42/ubuntu hardy partner

deb ftp://10.65.0.42/ubuntu/ hardy-security main restricted
deb-src ftp://10.65.0.42/ubuntu/ hardy-security main restricted
deb ftp://10.65.0.42/ubuntu/ hardy-security universe
deb-src ftp://10.65.0.42/ubuntu/ hardy-security universe
deb ftp://10.65.0.42/ubuntu/ hardy-security multiverse
deb-src ftp://10.65.0.42/ubuntu/ hardy-security multiverse

deb ftp://10.65.0.42/ubuntu hardy main universe multiverse
deb-src ftp://10.65.0.42/ubuntu hardy main universe multiverse

```
anyway to fix this problem.....have to get this ready b4 ibex

---

### Post by Hexagoon on 2008-10-22
You have used a LAN ip address (local), try to use the public ip address of the server and you will be set to go.

---

### Post by northern lights on 2008-10-22
This looks like a local IP. Doesn't the server have a WAN one too?

---

