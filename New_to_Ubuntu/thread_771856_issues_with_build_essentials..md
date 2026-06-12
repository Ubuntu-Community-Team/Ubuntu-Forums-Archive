---
title: "issues with build essentials."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-04-28
ok so I'm trying to install build essential and as i run the installer i keep on getting the same message

"error: dependancy is not satisfiable: libc6-dev libc-dev"

but i can install from the live cd.

 should i reinstall ubuntu?

 anything else i can do?

---

### Post by sam_delta on 2008-04-28
have you tried installing from the terminal?
go into the terminal and type
```
 sudo apt-get install build-essential 
```

sam

---

### Post by PatrickMoore on 2008-04-28
i get the error message "couldn't find any package whose name or description matched build essential" no packages will be installed upgraded or removed
anything else? i'm getting a tad frustrated with the brick wall i keep hitting

---

### Post by aysiu on 2008-04-28
Can you post the output of these commands? ```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by PatrickMoore on 2008-04-28
cat /etc/apt/sources.list produced...

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by PatrickMoore on 2008-04-28
sudo apt-get update produced...

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
patrick@patrick-laptop:~$

---

### Post by PatrickMoore on 2008-04-28
im using two computers to communicate as i don't have a wired connection with my laptop

---

### Post by sam_delta on 2008-04-28
you need internet connection to install build essential if you do not have internet connection, try downloading build essentials from 
[http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb)
, and copy and run the .deb package on your computer without network

---

### Post by aysiu on 2008-04-28
Okay. That's the problem. Right now the only software repository sources you have enabled are online ones, so if you don't have an online connection, you can't install *build-essential*.

We'll have to fix that. Paste in these commands: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo apt-cdrom add
``` You'll be prompted to insert a CD in your drive. Insert the Ubuntu CD. Then ```
sudo apt-get update
sudo apt-get install build-essential
```

**Edit**: Oops. Since you don't have a connection, you'll have to retype those commands instead of pasting them in.

---

### Post by PatrickMoore on 2008-04-28
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak...

 i get...

mv: missing destination file operand after '/etc/apt/sources.list.bak

---

### Post by PatrickMoore on 2008-04-28
and i think build essential is installed do you want me to post the terminal to make sure?

---

### Post by aysiu on 2008-04-28
> **PatrickMoore said:**
> sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak...

 i get...

mv: missing destination file operand after '/etc/apt/sources.list.bak
Perhaps you're missing the space between */etc/apt/sources.list* and */etc/apt/sources.list.bak*?

You're basically saying "Rename this sources.list file to sources.list.bak."

---

### Post by PatrickMoore on 2008-04-28
sudo apt-get update::: 

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
  Could not resolve 'security.ubuntu.com' 
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/main Translation-en_US 
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/restricted Translation-en_US 
Reading package lists... Done 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Some index files failed to download, they have been ignored, or old ones used instead. 
W: You may want to run apt-get update to correct these problems

---

### Post by PatrickMoore on 2008-04-28
**patrick@patrick-laptop:~$ sudo apt-get install build-essential**
 resulted in...
 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl 
  linux-libc-dev patch 
Suggested packages: 
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg 
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc 
The following NEW packages will be installed: 
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev 
  libtimedate-perl linux-libc-dev patch 
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B/8179kB of archives. 
After this operation, 33.8MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Selecting previously deselected package linux-libc-dev. 
(Reading database ... 94957 files and directories currently installed.) 
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-16.30_amd64.deb) ... 
Selecting previously deselected package libc6-dev. 
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_amd64.deb) ... 
Selecting previously deselected package libstdc++6-4.2-dev. 
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_amd64.deb) ... 
Selecting previously deselected package g++-4.2. 
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_amd64.deb) ... 
Selecting previously deselected package g++. 
Unpacking g++ (from .../g++_4.2.3-1ubuntu3_amd64.deb) ... 
Selecting previously deselected package libtimedate-perl. 
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ... 
Selecting previously deselected package patch. 
Unpacking patch (from .../patch/patch_2.5.9-4_amd64.deb) ... 
Selecting previously deselected package dpkg-dev. 
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu3_all.deb) ... 
Selecting previously deselected package build-essential. 
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ... 
Setting up linux-libc-dev (2.6.24-16.30) ... 
Setting up libc6-dev (2.7-10ubuntu3) ... 
Setting up libtimedate-perl (1.1600-9) ... 
Setting up patch (2.5.9-4) ... 
Setting up dpkg-dev (1.14.16.6ubuntu3) ... 
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ... 
Setting up g++-4.2 (4.2.3-2ubuntu7) ... 
Setting up g++ (4:4.2.3-1ubuntu3) ... 

Setting up build-essential (11.3ubuntu1) ... 

sorry if im flooding the board with nonsense i just really want to get this to work

---

### Post by Oldsoldier2003 on 2008-04-28
no problem. the last line of your output indicates you successfully installed build-essential

---

### Post by PatrickMoore on 2008-04-28
thanks guys you are truly amazing

---

### Post by talsemgeest on 2008-04-28
Just a tip, when you are posting those long files, put [code] tags around them, just to save space a bit. Other than that, I'm glad you got your problem fixed. :)

---

