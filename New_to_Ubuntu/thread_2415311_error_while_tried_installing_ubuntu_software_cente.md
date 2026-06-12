---
title: "error while tried installing ubuntu software center"
date: 2019-03-24
forum: New to Ubuntu
---

### Post by pratap73 on 2019-03-24
```
sudo apt-get install software-center
[sudo] password for dp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: software-center-aptdaemon-plugins but it is not going to be installed
                   Depends: ubuntu-sso-client but it is not going to be installed
                   Depends: python-piston-mini-client (>= 0.1+bzr29) but it is not going to be installed
                   Depends: oneconf (>= 0.2.6) but it is not going to be installed
                   Depends: python-oneconf (>= 0.3) but it is not going to be installed or
                            oneconf (< 0.3) but it is not going to be installed
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
E: Unable to correct problems, you have held broken packages
```

---

### Post by wildmanne39 on 2019-03-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

