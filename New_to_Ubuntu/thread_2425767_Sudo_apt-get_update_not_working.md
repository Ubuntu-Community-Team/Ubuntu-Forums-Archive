---
title: "Sudo apt-get update *not working"
date: 2019-08-29
forum: New to Ubuntu
---

### Post by ktv123 on 2019-08-29
coming back to ubuntu after a decade or so, everything seems slow and only semi-functional. getting  this error when updating.
 
I have tried looking for someone with the same problem, to no success. if a thread exists please let me know!

 excited to get into this system again and learn.

 my goal is to run wine and/or dual boot so i can play some EVERQUEST again. [IMG]https://ubuntu-mate.community/images/emoji/google/slight_smile.png?v=9[/IMG]

```
k@k-OptiPlex-960:~$ sudo apt-get update
[sudo] password for k: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-updates InRelease [97.5 kB]    
Get:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) disco InRelease [6,255 B]       
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security InRelease [97.5 kB]     
Ign:5 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) disco InRelease           
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-backports InRelease [88.8 kB]  
Ign:7 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) disco InRelease          
Err:8 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) disco Release
  404  Not Found [IP: 91.189.95.83 80]
Err:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) disco InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Err:9 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) disco Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/gezakovacs/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) disco InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu disco InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by wildmanne39 on 2019-08-29
Hello and welcome back!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Bashing-om on 2019-08-29
ktv123; Welcome back 2

these:
[http://ppa.launchpad.net/gezakovacs/ppa/ubuntu/dists/](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu/dists/)
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/)
show that they have no support in 19.04 (disco) -

Remove these sources as doubtful that these PPAs will be fitted to support a short term release.

[INDENT]it is what it is
[/INDENT]

---

### Post by CatKiller on 2019-08-30
You also don't appear to have added the new Wine signing key, which changed at the end of last year.

```
wget -nc https://dl.winehq.org/wine-builds/winehq.key
sudo apt-key add winehq.key 
```

---

