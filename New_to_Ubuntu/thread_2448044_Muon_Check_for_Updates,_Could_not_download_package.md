---
title: "Muon Check for Updates, Could not download packages"
date: 2020-07-31
forum: New to Ubuntu
---

### Post by nginmu on 2020-07-31
Lubuntu 20.04 / Muon Package Manager Version 5.8.0

"Check for Updates" results in "Could not download packages"

I tried sudo apt-get update:

```

me@me-pc:~$ sudo apt-get update
[sudo] password for me: 
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease                             
Hit:3 http://security.ubuntu.com/ubuntu focal-security InRelease                           
Hit:4 http://archive.ubuntu.com/ubuntu focal-backports InRelease                           
Ign:5 http://dl.google.com/linux/earth/deb stable InRelease
Get:6 http://dl.google.com/linux/earth/deb stable Release [933 B]
Get:7 http://dl.google.com/linux/earth/deb stable Release.gpg [819 B]
Ign:7 http://dl.google.com/linux/earth/deb stable Release.gpg
Reading package lists... Done
W: GPG error: http://dl.google.com/linux/earth/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 78BD65473CB3BD13
E: The repository 'http://dl.google.com/linux/earth/deb stable Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
me@me-pc:~$ 

```

I had previously installed Google Earth by downloading the .deb direct from Google:

```

sudo dpkg -i ~/google-earth-pro-stable_current_amd64.deb

```

How can I fix Muon "Check for Updates"?

Is it possible, the Muon GUI "Check for Updates" is actually working fine except when it gets round to looking at the Google stuff?

---

### Post by Impavidus on 2020-08-01
Your package manager works fine, except when checking for updates from google. To fix it, use```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 78BD65473CB3BD13
```

[https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)

---

### Post by nginmu on 2020-08-01
Thanks for the link. All working fine now.

---

