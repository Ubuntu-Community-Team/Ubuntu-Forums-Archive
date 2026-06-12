---
title: "Errors caused by bad/old packages, HELP!!"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by Stanislav Yotov on 2013-06-01
I am facing similar problem.
The output of sudo apt-get update is:

```

Ign http://download.webmin.com sarge InRelease
Hit http://download.webmin.com sarge Release.gpg
Hit http://download.webmin.com sarge Release
Hit http://download.webmin.com sarge/contrib amd64 Packages
Ign http://download.webmin.com sarge/contrib TranslationIndex
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://us.archive.ubuntu.com natty Release.gpg
Ign http://debian.opennms.org stable InRelease
Ign http://download.webmin.com sarge/contrib Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates Release.gpg
Ign http://security.ubuntu.com natty-security InRelease
Ign http://download.webmin.com sarge/contrib Translation-en
Get:1 http://debian.opennms.org stable Release.gpg [198 B]
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge InRelease
Ign http://us.archive.ubuntu.com natty Release
Ign http://us.archive.ubuntu.com natty-updates Release
Get:2 http://debian.opennms.org stable Release [4,593 B]
Err http://debian.opennms.org stable Release

Ign http://security.ubuntu.com natty-security Release.gpg
Ign http://us.archive.ubuntu.com natty/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release.gpg
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/main amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security Release
Ign http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release
Ign http://security.ubuntu.com natty-security/main Sources/DiffIndex
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib amd64 Packages
Ign http://security.ubuntu.com natty-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/universe Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/multiverse Sources/DiffIndex
Ign http://security.ubuntu.com natty-security/main amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/restricted amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/universe amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/multiverse amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib TranslationIndex
Err http://us.archive.ubuntu.com natty/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Err http://us.archive.ubuntu.com natty-updates/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty-updates/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty-updates/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://security.ubuntu.com natty-security/main Sources
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com natty-security/restricted Sources
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com natty-security/universe Sources
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com natty-security/multiverse Sources
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com natty-security/main amd64 Packages
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com natty-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.181 80]
Err http://security.ubuntu.com natty-security/universe amd64 Packages
  404  Not Found [IP: 91.189.92.181 80]
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Err http://security.ubuntu.com natty-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.181 80]
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Translation-en
Fetched 199 B in 1s (111 B/s)
Reading package lists.... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://debian.opennms.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 57801F6F5B9EFD43

W: Failed to fetch http://debian.opennms.org/dists/stable/Release

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.190 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

The output of  cat /etc/lsb-release && uname -r 
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

2.6.38-16-server

```


The outup of  cat /etc/apt/sources.list

```


#

# deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted

#deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib

deb http://debian.opennms.org stable main
deb-src http://debian.opennms.org stable main


```

" ls /etc/apt/sources.list.d/ " does not output anything at all.

I also saw this [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release) , so I chaned the /etc/apt/sources.list to:
```


# 

# deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64  (20110426)]/ natty main restricted

#deb cdrom:[Ubuntu-Server 11.04 _Natty  Narwhal_ - Release amd64 (20110426)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes)  for how to upgrade to
# newer versions of the distribution.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty main restricted

## Major bug fix updates produced after the final  release of the
## distribution.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty-updates main restricted

## N.B. software from this repository is  ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software  in universe WILL NOT receive any
## review or updates from the Ubuntu  security team.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty-updates universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty-updates universe

## N.B. software from this repository is ENTIRELY  UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence.  Please satisfy yourself as to 
## your rights to use the software. Also,  please note that software in 
## multiverse WILL NOT receive any review or  updates from the Ubuntu
## security team.
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty-updates multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty-updates multiverse

## Uncomment the following two lines to add  software from the 'backports'
## repository.
## N.B. software from this  repository may not have been tested as
## extensively as that contained in  the main release, although it includes
## newer versions of some applications  which may provide useful features.
## Also, please note that software in  backports WILL NOT receive any review
## or updates from the Ubuntu security  team.
# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty-backports main restricted universe multiverse
# deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  natty-backports main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)  natty-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)  natty-security main restricted
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)  natty-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)  natty-security universe
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)  natty-security multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)  natty-security multiverse

## Uncomment the following two lines to add  software from Canonical's
## 'partner' repository.
## This software is not  part of Ubuntu, but is offered by Canonical and the
## respective vendors as  a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  natty partner

## Uncomment the following two lines to add software from  Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu,  but is offered by third-party
## developers who want to ship their latest  software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty  main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty  main

deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository)  sarge contrib
deb [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository)  sarge contrib 

deb [http://debian.opennms.org](http://debian.opennms.org) stable  main
deb-src [http://debian.opennms.org](http://debian.opennms.org) stable main



```


If I strip it to the very basics :
```

#

# deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted


## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ natty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ CODENAME-backports main restricted universe multiverse


```

I get

```

Ign http://old-releases.ubuntu.com natty InRelease
Ign http://old-releases.ubuntu.com natty-updates InRelease
Ign http://old-releases.ubuntu.com natty-security InRelease
Hit http://old-releases.ubuntu.com natty Release.gpg
Hit http://old-releases.ubuntu.com natty-updates Release.gpg
Hit http://old-releases.ubuntu.com natty-security Release.gpg
Hit http://old-releases.ubuntu.com natty Release
Hit http://old-releases.ubuntu.com natty-updates Release
Hit http://old-releases.ubuntu.com natty-security Release
Hit http://old-releases.ubuntu.com natty/main amd64 Packages
Hit http://old-releases.ubuntu.com natty/restricted amd64 Packages
Hit http://old-releases.ubuntu.com natty/universe amd64 Packages
Hit http://old-releases.ubuntu.com natty/multiverse amd64 Packages
Ign http://old-releases.ubuntu.com natty/main TranslationIndex
Ign http://old-releases.ubuntu.com natty/multiverse TranslationIndex
Ign http://old-releases.ubuntu.com natty/restricted TranslationIndex
Ign http://old-releases.ubuntu.com natty/universe TranslationIndex
Hit http://old-releases.ubuntu.com natty-updates/main amd64 Packages
Hit http://old-releases.ubuntu.com natty-updates/restricted amd64 Packages
Hit http://old-releases.ubuntu.com natty-updates/universe amd64 Packages
Hit http://old-releases.ubuntu.com natty-updates/multiverse amd64 Packages
Ign http://old-releases.ubuntu.com natty-updates/main TranslationIndex
Ign http://old-releases.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://old-releases.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://old-releases.ubuntu.com natty-updates/universe TranslationIndex
Hit http://old-releases.ubuntu.com natty-security/main amd64 Packages
Hit http://old-releases.ubuntu.com natty-security/restricted amd64 Packages
Hit http://old-releases.ubuntu.com natty-security/universe amd64 Packages
Hit http://old-releases.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://old-releases.ubuntu.com natty-security/main TranslationIndex
Ign http://old-releases.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://old-releases.ubuntu.com natty-security/restricted TranslationIndex
Ign http://old-releases.ubuntu.com natty-security/universe TranslationIndex
Ign http://old-releases.ubuntu.com natty/main Translation-en_US
Ign http://old-releases.ubuntu.com natty/main Translation-en
Ign http://old-releases.ubuntu.com natty/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com natty/multiverse Translation-en
Ign http://old-releases.ubuntu.com natty/restricted Translation-en_US
Ign http://old-releases.ubuntu.com natty/restricted Translation-en
Ign http://old-releases.ubuntu.com natty/universe Translation-en_US
Ign http://old-releases.ubuntu.com natty/universe Translation-en
Ign http://old-releases.ubuntu.com natty-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com natty-updates/main Translation-en
Ign http://old-releases.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com natty-updates/multiverse Translation-en
Ign http://old-releases.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com natty-updates/restricted Translation-en
Ign http://old-releases.ubuntu.com natty-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com natty-updates/universe Translation-en
Ign http://old-releases.ubuntu.com natty-security/main Translation-en_US
Ign http://old-releases.ubuntu.com natty-security/main Translation-en
Ign http://old-releases.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com natty-security/multiverse Translation-en
Ign http://old-releases.ubuntu.com natty-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com natty-security/restricted Translation-en
Ign http://old-releases.ubuntu.com natty-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com natty-security/universe Translation-en
Reading package lists... Done


```

---

### Post by oldos2er on 2013-06-01
Post moved to its own thread.

---

### Post by ibjsb4 on 2013-06-01
Natty has reached end of life and no longer supported.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Consider doing a fresh install.

---

### Post by Stanislav Yotov on 2013-06-01
If there is any possible way arround it I would rater do an upgrade. I know this version is not supported, I was trying to upgrade it however it cannot even update.

---

### Post by ibjsb4 on 2013-06-01
You can try an end of life upgrade, but you will be upgrading to 11.10 which has also reached EOL.  Then you must upgrade to 12.04.  This is a very questionable way to go.  Again, a fresh install is best.  This link is dated, but I think you will get the idea on how to do a EOL upgrade.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Stanislav Yotov on 2013-06-05
Thank you all.
I also found those two helpful links.
[http://askubuntu.com/questions/74653/how-can-i-remove-the-translation-entries-in-apt](http://askubuntu.com/questions/74653/how-can-i-remove-the-translation-entries-in-apt)
[http://askubuntu.com/tags/aptitude/hot](http://askubuntu.com/tags/aptitude/hot)

What doew this output mean?

```

Ign http://old-releases.ubuntu.com natty InRelease
Ign http://old-releases.ubuntu.com natty-updates InRelease
Ign http://old-releases.ubuntu.com natty-security InRelease
Hit http://old-releases.ubuntu.com natty Release.gpg
Hit http://old-releases.ubuntu.com natty-updates Release.gpg
Hit http://old-releases.ubuntu.com natty-security Release.gpg
Hit http://old-releases.ubuntu.com natty Release
Hit http://old-releases.ubuntu.com natty-updates Release
Hit http://old-releases.ubuntu.com natty-security Release
Hit http://old-releases.ubuntu.com natty/main amd64 Packages
Hit http://old-releases.ubuntu.com natty/restricted amd64 Packages
Hit http://old-releases.ubuntu.com natty/universe amd64 Packages
Hit http://old-releases.ubuntu.com natty/multiverse amd64 Packages
Ign http://old-releases.ubuntu.com natty/main TranslationIndex
Ign http://old-releases.ubuntu.com natty/multiverse TranslationIndex
Ign http://old-releases.ubuntu.com natty/restricted TranslationIndex
Ign http://old-releases.ubuntu.com natty/universe TranslationIndex
Hit http://old-releases.ubuntu.com natty-updates/main amd64 Packages
Hit http://old-releases.ubuntu.com natty-updates/restricted amd64 Packages
Hit http://old-releases.ubuntu.com natty-updates/universe amd64 Packages
Hit http://old-releases.ubuntu.com natty-updates/multiverse amd64 Packages
Ign http://old-releases.ubuntu.com natty-updates/main TranslationIndex
Ign http://old-releases.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://old-releases.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://old-releases.ubuntu.com natty-updates/universe TranslationIndex
Hit http://old-releases.ubuntu.com natty-security/main amd64 Packages
Hit http://old-releases.ubuntu.com natty-security/restricted amd64 Packages
Hit http://old-releases.ubuntu.com natty-security/universe amd64 Packages
Hit http://old-releases.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://old-releases.ubuntu.com natty-security/main TranslationIndex
Ign http://old-releases.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://old-releases.ubuntu.com natty-security/restricted TranslationIndex
Ign http://old-releases.ubuntu.com natty-security/universe TranslationIndex
Reading package lists... Done


```

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]Stanislav Yotov Hi !

That output I would deem as the regenerated /etc/apt/sources.list so that the package manager is now pointed to the End Of Life "natty" repository, I would expect when you do this version upgrade to onieric, that the process will be repeated, and upon the next "upgrade" to finally be precise.( and hope nothing breaks in all these processes )
[/COLOR][INDENT=3][COLOR=#000000]
kind regards
 [/COLOR][/INDENT]

---

### Post by snowpine on 2013-06-05
I echo the recommendation to back up your files and do a fresh resinstall of a supported release (12.04 or newer).

If you **must** upgrade, then a good start is to delete all of your Debian Sarge software sources!!! (completely unsuppored since 2008)

---

### Post by Stanislav Yotov on 2013-06-22
I did the upgrade to 12.04. The apache server had an issue, however I had done proper back up, using rsync, and I was able to recover from it.
For the upgrade I followed the [tutorial]("https://help.ubuntu.com/community/EOLUpgrades") sugested by [**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120").
During the instalation of the "update-manager-core", there was a problem with some software.
**[SIZE=3] [SIZE=2]ERROR: Module fcgid does not exist!         [/SIZE][/SIZE]**

I used:
```
 sudo apt-get purge libapache2-mod-fcgid 
```
in order to remove it and then 
 ```
 sudo apt-get install libapache2-mod-fcgid 
```
in order to install it and then I tried to install "update-manager-core", and it worked.
```
 sudo apt-get install update-manager-core 
```

afterward I was able to perform the actual upgrade to 11.10 and later to 12.04.
```
 sudo do-release-upgrade 
```

Everything turned ok. 

Thank you all for the help!

---

