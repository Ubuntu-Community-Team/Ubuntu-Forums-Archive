---
title: "can't install wine-1.3.33.tar.bz2"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by kam_ctrl on 2012-01-23
how to install wine in ubuntu using downloaded wine-1.3.33.tar.bz2. i have run the wineinstall but nothing happen. when i run wineinstall using terminal, it show some loading then suddenly disappear..so need help..huhu

---

### Post by BC59 on 2012-01-23
The best way to install Wine 1.3 is through the Wine repository:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update && sudo apt-get install wine1.3
```

---

### Post by kam_ctrl on 2012-01-23
tq..but i have try that..it stuck at some level..and when i use ubuntu software center, it hang at 12mb..both wine 1.2 and wine 1.3..

---

### Post by kam_ctrl on 2012-01-23
btw..how to solve this problem

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG A6804EA8EAE0D85C Launchpad PPA for Nate Muench
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG 5A9A06AEF9CB8DB0 Launchpad PPA for Ubuntu Wine Team
W: GPG error: [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index](http://my.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/my.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Index](http://my.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/my.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index](http://my.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/my.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index

W: Failed to fetch [http://my.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Index](http://my.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/my.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index
E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by BC59 on 2012-01-23
Run these commands:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
```

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A6804EA8EAE0D85C
gpg --export --armor A6804EA8EAE0D85C | sudo apt-key add -
```

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
gpg --export --armor 5A9A06AEF9CB8DB0 | sudo apt-key add -
```

---

### Post by sandyd on 2012-01-23
> **kam_ctrl said:**
> tq..but i have try that..it stuck at some level..and when i use ubuntu software center, it hang at 12mb..both wine 1.2 and wine 1.3..
a) Check your internet.
b) For the other unfetchable problems, try changing the mirror to "Main archive" (or whatever its called now, I don't use Ubuntu on Desktop) in software sources.

---

