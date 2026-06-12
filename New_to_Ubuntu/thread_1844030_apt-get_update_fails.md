---
title: "apt-get update fails"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by DSn0wMan on 2011-09-14
Not sure whats going on, it's almost like I have something cached, and i cant get rid of it.

I have tried the following, and still can not download any updates.

```

sudo apt-get clean
sudo apt-get update -o Acquire::http::No-Cache=True
sudo apt-get update -o Acquire::BrokenProxy=true

```

I can get to the gpg files just using firefox, but somehow apt cant resolve them.

ex...

[http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg) works for me in firefox.

```

Ign http://archive.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty-updates InRelease 
Ign http://archive.ubuntu.com natty-security InRelease
Err http://archive.ubuntu.com natty Release.gpg
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-updates Release.gpg
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-security Release.gpg
  Connection failed [IP: 91.189.88.40 80]
Ign http://archive.ubuntu.com natty Release          
Ign http://archive.ubuntu.com natty-updates Release
Ign http://archive.ubuntu.com natty-security Release
Ign http://archive.ubuntu.com natty/main TranslationIndex
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty/restricted TranslationIndex
Ign http://archive.ubuntu.com natty/universe TranslationIndex
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://archive.ubuntu.com natty-security/main TranslationIndex
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Err http://archive.ubuntu.com natty/main Sources     
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty/restricted Sources
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty/universe Sources
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty/multiverse Sources
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty/main i386 Packages
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty/restricted i386 Packages
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty/universe i386 Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty/multiverse i386 Packages
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-updates/main Sources
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-updates/restricted Sources
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-updates/universe Sources
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-updates/multiverse Sources
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-updates/main i386 Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-updates/restricted i386 Packages
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-updates/universe i386 Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-updates/multiverse i386 Packages
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-security/main Sources
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-security/restricted Sources
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-security/universe Sources
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-security/multiverse Sources
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-security/main i386 Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-security/restricted i386 Packages
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-security/universe i386 Packages
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-security/multiverse i386 Packages
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty/main Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty/main Translation-en
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty/multiverse Translation-en_US
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty/multiverse Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty/restricted Translation-en_US
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty/restricted Translation-en
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty/universe Translation-en_US
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty/universe Translation-en
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-updates/main Translation-en_US
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-updates/main Translation-en
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-updates/multiverse Translation-en
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-updates/restricted Translation-en_US
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-updates/restricted Translation-en
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-updates/universe Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-updates/universe Translation-en
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-security/main Translation-en_US
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-security/main Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-security/multiverse Translation-en_US
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-security/multiverse Translation-en
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-security/restricted Translation-en_US
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-security/restricted Translation-en
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-security/universe Translation-en_US
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-security/universe Translation-en
  Connection failed [IP: 91.189.88.31 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_US  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_US  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_US  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_US  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_US  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_US  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_US  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_US  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_US  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_US  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_US  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en  Connection failed [IP: 91.189.88.31 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by DSn0wMan on 2011-09-19
I still can't solve this problem. Is there some way to completely reset apt. I don't care too much about my PPA's but I need to be able to get some sort of updates.

---

### Post by wildmanne39 on 2011-09-19
Hi, you can try this if it does not work you night just open synaptic and uncheck the ppa's that are giving you problems.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
Thank you

---

### Post by el_koraco on 2011-09-19
Did you try just changing the download server?

---

### Post by DSn0wMan on 2011-09-19
> **el_koraco said:**
> Did you try just changing the download server?

I tried switching back and forth between US and Main, but that didn't help at all.

---

### Post by DSn0wMan on 2011-09-19
> **wildmanne39 said:**
> Hi, you can try this if it does not work you night just open synaptic and uncheck the ppa's that are giving you problems.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
Thank you

I have removing files from /var/lib/apt/lists, but I am still not able to update.

I have also unchecked all my ppa's. The problem is that none of the regular repositories are working either.

```

Err http://archive.ubuntu.com natty Release.gpg
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-updates Release.gpg
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-security Release.gpg
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty/main Sources      
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty/restricted Sources
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty/universe Sources
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty/multiverse Sources
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty/main i386 Packages
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty/restricted i386 Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty/universe i386 Packages
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty/multiverse i386 Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-updates/main Sources
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-updates/restricted Sources
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-updates/universe Sources
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-updates/multiverse Sources
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-updates/main i386 Packages
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-updates/restricted i386 Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-updates/universe i386 Packages
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-updates/multiverse i386 Packages
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-security/main Sources
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-security/restricted Sources
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-security/universe Sources
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-security/multiverse Sources
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-security/main i386 Packages
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-security/restricted i386 Packages
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-security/universe i386 Packages
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-security/multiverse i386 Packages
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty/main Translation-en_US
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty/main Translation-en
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty/multiverse Translation-en_US
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty/multiverse Translation-en
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty/restricted Translation-en_US
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty/restricted Translation-en
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty/universe Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty/universe Translation-en
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-updates/main Translation-en_US
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-updates/main Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-updates/multiverse Translation-en
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-updates/restricted Translation-en_US
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-updates/restricted Translation-en
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-updates/universe Translation-en_US
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-updates/universe Translation-en
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-security/main Translation-en_US
  Connection failed [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com natty-security/main Translation-en
  Connection failed [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com natty-security/multiverse Translation-en_US
  Connection failed [IP: 91.189.92.171 80]
Err http://archive.ubuntu.com natty-security/multiverse Translation-en
  Connection failed [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com natty-security/restricted Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com natty-security/restricted Translation-en
  Connection failed [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com natty-security/universe Translation-en_US
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com natty-security/universe Translation-en
  Connection failed [IP: 91.189.88.45 80]

```

---

### Post by wildmanne39 on 2011-09-19
Hi, please post the results of these commands here.
```
cat /etc/apt/sources.list
```
```
ls /etc/apt/sources.list.d/
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by DSn0wMan on 2011-09-19
```

grayjo@asg-jp95yc1:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Beta i386 (20110413)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main
# deb http://archive.canonical.com/ natty partner
# deb-src http://archive.canonical.com/ natty partner
# deb http://download.virtualbox.org/virtualbox/debian natty contrib

```
```

grayjo@asg-jp95yc1:~$ ls /etc/apt/sources.list.d/
am-monkeyd-nautilus-elementary-ppa-natty.list       nilarimogard-webupd8-natty.list.save
am-monkeyd-nautilus-elementary-ppa-natty.list.save  opera.list
banshee-team-banshee-daily-natty.list               opera.list.save
banshee-team-banshee-daily-natty.list.save          paulo-miguel-dias-tomahawk-natty.list
bisigi-ppa-natty.list                               paulo-miguel-dias-tomahawk-natty.list.save
bisigi-ppa-natty.list.save                          postler-dev-ppa-natty.list
conky-companions-ppa-natty.list                     postler-dev-ppa-natty.list.save
conky-companions-ppa-natty.list.save                tiheum-equinox-natty.list
ddebs.list                                          tiheum-equinox-natty.list.save
ddebs.list.save                                     tualatrix-ppa-natty.list
elementaryart-elementarydesktop-natty.list          tualatrix-ppa-natty.list.save
elementaryart-elementarydesktop-natty.list.save     ubuntu-tweak-stable.list.save
google-chrome.list                                  ubuntu-wine-ppa-natty.list
google-chrome.list.save                             ubuntu-wine-ppa-natty.list.save
google-musicmanager.list                            virtualbox.list
google-musicmanager.list.save                       virtualbox.list.save
nilarimogard-webupd8-natty.list

```

---

### Post by tgm4883 on 2011-09-19
Can you open 91.189.92.171 in a web browser?

---

### Post by DSn0wMan on 2011-09-19
> **tgm4883 said:**
> Can you open 91.189.92.171 in a web browser?

Yes

---

### Post by wildmanne39 on 2011-09-19
Give me a few minutes while I compare your list to mine.
Thank you

---

### Post by neojames on 2011-09-19
Just like to say that I'm getting the same problem on my Laptop running Oneiric, but not a peep on my Desktop with Natty.

---

### Post by wildmanne39 on 2011-09-19
Hi, I suggest you go to this link and regenerate your source list and start with a new one.
[http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html](http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html)
Thank you

---

### Post by wildmanne39 on 2011-09-19
Hi, also you did not start using a proxy did you? there is trouble with updates and proxy.
Thank you

---

### Post by DSn0wMan on 2011-09-19
> **wildmanne39 said:**
> Hi, I suggest you go to this link and regenerate your source list and start with a new one.
[http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html](http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html)
Thank you

I just updated my sources.list to something extremely simple, and I am still getting the same problems.


###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

---

### Post by DSn0wMan on 2011-09-19
> **wildmanne39 said:**
> Hi, also you did not start using a proxy did you? there is trouble with updates and proxy.
Thank you

I don't think so, but this is a corporate environment, so it's possible the network guys are getting tricky with me.

Also I am pretty sure there has always been a filter between me and the web., so there is some sort of proxy, but this was previously working, and I can go to the sites through a browser, so I know I am not being blocked.

---

### Post by wildmanne39 on 2011-09-19
Hi, but when you click on the links you posted you can get to them correct?
Thank you

---

### Post by DSn0wMan on 2011-09-19
> **wildmanne39 said:**
> Hi, but when you click on the links you posted you can get to them correct?
Thank you

Correct

---

### Post by wildmanne39 on 2011-09-19
Hi, There is sure something strange going on I have never seen that exact error, it looks like your ip adsdress is being blocked from getting the updates, maybe a new firewall setting or proxy.
Thank you

---

### Post by DSn0wMan on 2011-09-19
> **wildmanne39 said:**
> Hi, There is sure something strange going on I have never seen that exact error, it looks like your ip adsdress is being blocked from getting the updates, maybe a new firewall setting or proxy.
Thank you

That's likely. There really were not any changes on my machine locally except it went down hard during a power outage, and when it came back up I cant get updates. 

I can get to the sites, so it's not like they are actively blocking archive.ubuntu.com or something. Just drives me nuts that my browser resolves the repositories fine, but apt-get doesn't.

---

### Post by wildmanne39 on 2011-09-19
Hi, I have seen problems getting updates after hard shut down before but usually we see input output errors I believe.

I have been researching this issue this whole time but I am not finding anything useful so far.

You may want to see if you have bad sectors on your hard drive after the hard shut down that is what usually causes these problems when the system is not shut down properly, files get corrupted.
Thank you

---

### Post by DSn0wMan on 2011-09-19
> **wildmanne39 said:**
> Hi, I have seen problems getting updates after hard shut down before but usually we see input output errors I believe.

I have been researching this issue this whole time but I am not finding anything useful so far.

You may want to see if you have bad sectors on your hard drive after the hard shut down that is what usually causes these problems when the system is not shut down properly, files get corrupted.
Thank you

I forced fdsk to do a check disk on reboot, but it didn't correct the problem.

Is there something in how apt-get update makes the request to the repositories that is different than a regular http call. I am just trying to grasp whats happening so i can speak intelligently to our Network admins.

---

### Post by wildmanne39 on 2011-09-19
Hi, not that I know of.

You can open disk utility and run a smart test on your drive it will tell you have bad sectors.
Thank you

---

### Post by DSn0wMan on 2011-09-19
> **wildmanne39 said:**
> Hi, not that I know of.

You can open disk utility and run a smart test on your drive it will tell you have bad sectors.
Thank you

Looks like I have 15 bad sectors. If I look at the details it says
"Uncorrectable Sector Count" has a value of 15.

Is there some way of fixing the bad sectors?

---

### Post by wildmanne39 on 2011-09-19
Hi, no there is not, the best thing to do is back up all your important files and reformat that will block the bad sectors so no more files get put in there, then reinstall ubuntu.

Some one else might have a better idea, but I do not believe so.

That is most likely the cause of your issue, files for updating are in the bad sectors.
Thank you

---

### Post by DSn0wMan on 2011-09-19
> **wildmanne39 said:**
> Hi, no there is not, the best thing to do is back up all your important files and reformat that will block the bad sectors so no more files get put in there, then reinstall ubuntu.

Some one else might have a better idea, but I do not believe so.

That is most likely the cause of your issue, files for updating are in the bad sectors.
Thank you

That's pretty much what I expected. Hopefully the bad sectors are in "/" and not "/home". I guess it's a good time to upgrade to 11.10.

---

### Post by wildmanne39 on 2011-09-19
Hi, the upgrade to 11.10 is up to you, I have been testing it and right now it will not run on my system at all, I suspect it is the nvidia driver.
Thank you

---

### Post by DSn0wMan on 2011-09-19
It's gotta be a network change or something cached in my /home partition since I get the same errors on a clean install.

---

### Post by wildmanne39 on 2011-09-19
Hi, I am sorry to hear the install did not fix it, that is not what I expected.

---

### Post by DSn0wMan on 2011-09-20
> **wildmanne39 said:**
> Hi, I am sorry to hear the install did not fix it, that is not what I expected.

I got a hold of the other guy in the company who runs ubuntu, and he's getting the same errors, so it must be something network related like a new proxy setting. In any case I installed Fedora for now which updates just fine. It might be a better fit for work since there a lot supported redhat 5 desktops out there.

---

### Post by wildmanne39 on 2011-09-20
Hi, I am glad you have the matter resolved.
Thank you

---

### Post by solbjorn on 2012-04-05
hej, 
i am having the exact same problem. does anyone know by now how i can solve this on ubuntu?

---

### Post by DSn0wMan on 2012-04-05
> **solbjorn said:**
> hej, 
i am having the exact same problem. does anyone know by now how i can solve this on ubuntu?

The problem I was having was due to some new proxy settings which magically changed after mentioning something to the Network admins. Sorry I don't have anything more helpful to say.

---

### Post by solbjorn on 2012-04-05
thanks for responding. 
how could i change my proxy settings back?

---

### Post by woxuxow on 2012-04-05
The network supervisor should change back the setting not you 
you just ask him/his to change back or tells you the configure setting

---

### Post by solbjorn on 2012-04-06
thank you  :) 
i wil try that

---

### Post by solbjorn on 2012-04-06
ok the problem somehow vanished without any of my doing :o :D

---

### Post by woxuxow on 2012-04-06
> **solbjorn said:**
> ok the problem somehow vanished without any of my doing :o :D

excellent

---

### Post by dtohjam on 2012-06-25
PARTLY SOLVED;
I've suffered the same problem of apt-get, synaptic etc failing to connect to the repositories.  So as to distinguish this issue from others I get these messages:

With synaptic; 
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/precise/InRelease)  

With sudo apt-get update;
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise InRelease 
[Waiting for headers] [Waiting for headers] [Waiting for headers]  ; and

Using doing an update (check) Ubuntu 12.04 Update Manager appears to work!

An error message (hours ago and I can't remember where) said that I failed to connect to the repository at _localhost:4001_.  I'm able to ping the repository and access with my web browser.  So it appears that apt-get is routed via a local proxy.

I've deleted and reconstructed the /etc/apt/sources.list

I've checked /etc/environment and see that it includes;
# +ANON_MARK+ Don't change this while anon-proxy manages this variable.
# +ANON_MARK+ To take back control of it run dpkg-reconfigure and tell
# +ANON_MARK+ debconf not to set this variable for you.
HTTP_PROXY=http://localhost:4001 # +ANON_MARK+
http_proxy=http://localhost:4001 # +ANON_MARK+

I've just #'ed out the last two lines and all seems to work ok.

Can any one explain what is ANON_MARK and why is the proxy added, and is there a proper way to correct this addition?

Thanks

---

### Post by tgm4883 on 2012-06-25
> **dtohjam said:**
> PARTLY SOLVED;
I've suffered the same problem of apt-get, synaptic etc failing to connect to the repositories.  So as to distinguish this issue from others I get these messages:

With synaptic; 
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/precise/InRelease)  

With sudo apt-get update;
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise InRelease 
[Waiting for headers] [Waiting for headers] [Waiting for headers]  ; and

Using doing an update (check) Ubuntu 12.04 Update Manager appears to work!

An error message (hours ago and I can't remember where) said that I failed to connect to the repository at _localhost:4001_.  I'm able to ping the repository and access with my web browser.  So it appears that apt-get is routed via a local proxy.

I've deleted and reconstructed the /etc/apt/sources.list

I've checked /etc/environment and see that it includes;
# +ANON_MARK+ Don't change this while anon-proxy manages this variable.
# +ANON_MARK+ To take back control of it run dpkg-reconfigure and tell
# +ANON_MARK+ debconf not to set this variable for you.
HTTP_PROXY=http://localhost:4001 # +ANON_MARK+
http_proxy=http://localhost:4001 # +ANON_MARK+

I've just #'ed out the last two lines and all seems to work ok.

Can any one explain what is ANON_MARK and why is the proxy added, and is there a proper way to correct this addition?

Thanks

ANON_MARK appears to be from the anon-proxy package, which is something you would have to had installed as it doesn't come by default.

---

