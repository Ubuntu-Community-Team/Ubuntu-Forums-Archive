---
title: "Problem with aptdaemon"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by cirgue on 2012-04-01
I'm trying to install Arabic language support through System Settings -> Language Support-> Install/remove languages. 

before the installation began, I got a dialog box saying that there is a problem with aptdaemon, and it gave  me this error message:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


I then tried updating the repositories with the blind hope that this might help, and got the following message;

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.167 80]

I've tried several of the fixes already listed in the forum for the GPG error, but nothing has worked so far. 

I tried installing the Arabic pack again just for giggles, and got the same message as before.


What's going on, and how do I fix it?

---

### Post by raja.genupula on 2012-04-01
open your terminal and do this

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

execute them one by one .

all the best .

---

### Post by raja.genupula on 2012-04-01
open your terminal and do this

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

execute them one by one .

all the best .

---

### Post by cirgue on 2012-04-04
Hey Raja,

Thanks for the help. It seems to have solved one problem and revealed another. I now get a few of these when I try to update:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Index](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_i18n_Index

When I try add a language pack, I get the same error message as before.

---

