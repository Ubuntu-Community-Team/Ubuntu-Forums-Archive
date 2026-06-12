---
title: "trouble with apt"
date: 2024-06-12
forum: New to Ubuntu
---

### Post by filiprybar on 2024-06-12
Hi there, I tried to install some apt packages and then I ran sudo apt update.
output was
```
Hit:1 [http://sk.archive.ubuntu.com/ubuntu](http://sk.archive.ubuntu.com/ubuntu) noble InRelease
Hit:2 [http://sk.archive.ubuntu.com/ubuntu](http://sk.archive.ubuntu.com/ubuntu) noble-updates InRelease              
Hit:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) noble InRelease                 
Hit:4 [http://sk.archive.ubuntu.com/ubuntu](http://sk.archive.ubuntu.com/ubuntu) noble-backports InRelease            
Hit:5 [https://ppa.launchpadcontent.net/kisak/kisak-mesa/ubuntu](https://ppa.launchpadcontent.net/kisak/kisak-mesa/ubuntu) noble InRelease 
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security InRelease               
Reading package lists... Done
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list:1 and /etc/apt/sources.list.d/winehq-noble.sources:1
```

---

### Post by deadflowr on 2024-06-12
It's telling you that you have the same source in multiple places.
Look at /etc/apt/sources.list.d and remove one of the listed sources for wine.
one is marked as a list file and the other is marked as a sources file.

These
/etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_-noble.list
/etc/apt/sources.list.d/winehq-noble.sources

You should be able to rm either one of them.

---

### Post by grahammechanical on 2024-06-12
Another way to do this is to open Software & Updates>Other Software tab and see what is listed there.

On my Ubuntu 24.04 LTS is see:

> [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) noble main

That line is ticked. It is all I need to have Wine installed and to get updates. You will see extra lines for Wine. Un-tick them. If that solves the problem you can them use Software & Updates to remove those unnecessary sources of software repositories.

Regards

---

### Post by filiprybar on 2024-06-12
Thank you deadflowr, this was a flawlessly solve for my issue.

---

