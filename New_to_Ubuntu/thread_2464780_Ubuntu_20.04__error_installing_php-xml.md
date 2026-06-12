---
title: "Ubuntu 20.04 : error installing php-xml"
date: 2021-07-12
forum: New to Ubuntu
---

### Post by maketopsite on 2021-07-12
```
apt-get install php-xml
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  php7.4-xml
The following NEW packages will be installed:
  php-xml php7.4-xml
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 99,3 kB of archives.
After this operation, 457 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://at.archive.ubuntu.com/ubuntu focal-updates/main amd64 php7.4-xml amd64 7.4.3-4ubuntu2.5 [97,3 kB]
Get:2 http://at.archive.ubuntu.com/ubuntu focal/main amd64 php-xml all 2:7.4+75 [2&#8239;028 B]
Ign:1 http://at.archive.ubuntu.com/ubuntu focal-updates/main amd64 php7.4-xml amd64 7.4.3-4ubuntu2.5
Ign:2 http://at.archive.ubuntu.com/ubuntu focal/main amd64 php-xml all 2:7.4+75
Err:2 http://at.archive.ubuntu.com/ubuntu focal/main amd64 php-xml all 2:7.4+75
  File has unexpected size (48322 != 97268). Mirror sync in progress? [IP: x2xx:xxxx:x:xxx:x::2 443]
Err:1 http://at.archive.ubuntu.com/ubuntu focal-updates/main amd64 php7.4-xml amd64 7.4.3-4ubuntu2.5
  File has unexpected size (48322 != 97268). Mirror sync in progress? [IP: x2xx:xxxx:x:xxx:x::2 443]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php7.4/php7.4-xml_7.4.3-4ubuntu2.5_amd64.deb  File has unexpected size (48322 != 97268). Mirror sync in progress? [IP: x2xx:xxxx:x:xxx:x::2 443]
E: Failed to fetch http://at.archive.ubuntu.com/ubuntu/pool/main/p/php-defaults/php-xml_7.4+75_all.deb  File has unexpected size (48322 != 97268). Mirror sync in progress? [IP: x2xx:xxxx:x:xxx:x::2 443]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

```
apt-get update
Hit:4 https://download.docker.com/linux/ubuntu focal InRelease                                                                                            
Get:1 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease [48,3 kB]                                                                      
Get:2 http://at.archive.ubuntu.com/ubuntu focal InRelease [48,3 kB]
Get:3 http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal InRelease [48,3 kB]
Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [48,3 kB]
Get:6 http://at.archive.ubuntu.com/ubuntu focal-updates InRelease [48,3 kB]
Err:1 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:2 http://at.archive.ubuntu.com/ubuntu focal InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:3 http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:5 http://security.ubuntu.com/ubuntu focal-security InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:6 http://at.archive.ubuntu.com/ubuntu focal-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:7 http://at.archive.ubuntu.com/ubuntu focal-backports InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Reading package lists... Done       
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease' is no longer signed.
E: Failed to fetch http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/focal/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://at.archive.ubuntu.com/ubuntu focal InRelease' is no longer signed.
E: Failed to fetch http://at.archive.ubuntu.com/ubuntu/dists/focal/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://ppa.launchpad.net/slimbook/slimbook/ubuntu focal InRelease' is no longer signed.
E: Failed to fetch http://ppa.launchpad.net/slimbook/slimbook/ubuntu/dists/focal/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://security.ubuntu.com/ubuntu focal-security InRelease' is no longer signed.
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch http://at.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://at.archive.ubuntu.com/ubuntu focal-updates InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://at.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://at.archive.ubuntu.com/ubuntu focal-backports InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


```

Any idea pls ?

---

