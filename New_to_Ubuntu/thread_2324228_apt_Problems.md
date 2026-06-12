---
title: "apt Problems"
date: 2016-05-12
forum: New to Ubuntu
---

### Post by G4143 on 2016-05-12
When I run sudo apt-get I get these errors. Can anyone tell how I can address and correct them? Ubuntu 16.04

```
Hit:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]                                                                                                                               
Ign:3 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial InRelease                                                                                                                               
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                                                                                                                                         
Hit:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-backports InRelease                                                                                 
Hit:6 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                                                               
Hit:7 [http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu) xenial InRelease                                  
Ign:8 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial Release                   
Ign:9 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 Packages       
Hit:10 [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy InRelease                         
Ign:11 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main i386 Packages
Ign:12 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main all Packages
Ign:13 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en_CA
Ign:14 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en
Ign:15 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:16 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:9 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 Packages
Ign:11 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main i386 Packages
Ign:12 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main all Packages
Ign:13 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en_CA
Ign:14 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en
Ign:15 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:16 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:9 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 Packages
Ign:11 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main i386 Packages
Ign:12 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main all Packages
Ign:13 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en_CA
Ign:14 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en
Ign:15 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:16 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:9 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 Packages
Ign:11 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main i386 Packages
Ign:12 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main all Packages
Ign:13 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en_CA
Ign:14 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en
Ign:15 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:16 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:9 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 Packages
Ign:11 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main i386 Packages
Ign:12 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main all Packages
Ign:13 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en_CA
Ign:14 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en
Ign:15 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:16 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Err:9 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 Packages
  404  Not Found
Err:11 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main i386 Packages
  404  Not Found
Ign:12 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main all Packages
Ign:13 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en_CA
Ign:14 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main Translation-en
Ign:15 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:16 [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Fetched 94.5 kB in 4s (20.4 kB/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-lxc/lxd-stable/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by deadflowr on 2016-05-12
Disable/remove the lxc ppa, as it does not exist for 16.04.

---

### Post by Bucky Ball on 2016-05-12
Also, an aside, you only need

> sudo apt update

... in 16.04. Not need for the '-get'. ;)

And as per deadflowr's advice, disable/remove the lxc ppa.

---

### Post by G4143 on 2016-05-12
Its odd that I had to remove/disable lxc ppa because I did a clean install of Ubuntu 16.04.

---

### Post by grahammechanical on 2016-05-12
Did you format the partition?

Regards

---

### Post by G4143 on 2016-05-12
Yes I formated the entire drive when I installed.

---

### Post by ian-weisser on 2016-05-12
After you did a clean install, you clearly did some customization.
That customization included installing PPAs, two of which are still enabled: webupd8team and ubuntu-lxc.
PPAs are not included with a clean install. Never have been, never will be. Everything for a clean install is in Main.

No PPAs were included with my 16.04.

---

