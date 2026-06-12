---
title: "Unable to locate package git"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by hichits on 2014-07-29
apt-get install git
Reading package lists... Done
Building dependency tree
Reading state information... Done
[COLOR=#ff0000]E: Unable to locate package git[/COLOR]

From the forum noticed it is solved by doing an update but update is failing as well.....not sure what is wrong with my /etc/apt/source-list

```
sudo apt-get update && sudo apt-get upgrade


Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
Ign mirror://mirrors.ubuntu.com trusty InRelease
Ign mirror://mirrors.ubuntu.com trusty-updates InRelease
Ign mirror://mirrors.ubuntu.com trusty-backports InRelease
Ign mirror://mirrors.ubuntu.com trusty-security InRelease
Ign mirror://mirrors.ubuntu.com trusty Release.gpg
Ign mirror://mirrors.ubuntu.com trusty-updates Release.gpg
Ign mirror://mirrors.ubuntu.com trusty-backports Release.gpg
Ign mirror://mirrors.ubuntu.com trusty-security Release.gpg
Ign mirror://mirrors.ubuntu.com trusty Release
Ign mirror://mirrors.ubuntu.com trusty-updates Release
Ign mirror://mirrors.ubuntu.com trusty-backports Release
Ign mirror://mirrors.ubuntu.com trusty-security Release
Err mirror://mirrors.ubuntu.com trusty/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com trusty/main Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty/main Translation-en
Ign mirror://mirrors.ubuntu.com trusty/multiverse Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty/multiverse Translation-en
Ign mirror://mirrors.ubuntu.com trusty/restricted Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty/restricted Translation-en
Ign mirror://mirrors.ubuntu.com trusty/universe Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty/universe Translation-en
Err mirror://mirrors.ubuntu.com trusty-updates/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-updates/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-updates/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-updates/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com trusty-updates/main Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-updates/main Translation-en
Ign mirror://mirrors.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-updates/multiverse Translation-en
Ign mirror://mirrors.ubuntu.com trusty-updates/restricted Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-updates/restricted Translation-en
Ign mirror://mirrors.ubuntu.com trusty-updates/universe Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-updates/universe Translation-en
Err mirror://mirrors.ubuntu.com trusty-backports/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-backports/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-backports/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-backports/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com trusty-backports/main Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-backports/main Translation-en
Ign mirror://mirrors.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-backports/multiverse Translation-en
Ign mirror://mirrors.ubuntu.com trusty-backports/restricted Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-backports/restricted Translation-en
Ign mirror://mirrors.ubuntu.com trusty-backports/universe Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-backports/universe Translation-en
Err mirror://mirrors.ubuntu.com trusty-security/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-security/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-security/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com trusty-security/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com trusty-security/main Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-security/main Translation-en
Ign mirror://mirrors.ubuntu.com trusty-security/multiverse Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-security/multiverse Translation-en
Ign mirror://mirrors.ubuntu.com trusty-security/restricted Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-security/restricted Translation-en
Ign mirror://mirrors.ubuntu.com trusty-security/universe Translation-en_US
Ign mirror://mirrors.ubuntu.com trusty-security/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe i386 Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Translation-en
W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/main/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/restricted/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/universe/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/multiverse/source/Sources)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/restricted/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/universe/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/multiverse/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by hichits on 2014-07-29
Found answer to my problem , my /etc/apt/apt.conf file was having an entry for proxy and the proxy url had a typo.

---

### Post by mörgæs on 2014-07-29
Good, please mark the thread 'solved'.

---

