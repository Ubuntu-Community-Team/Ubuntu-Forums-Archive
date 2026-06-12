---
title: "problem installing plugins gstreamer"
date: 2019-04-01
forum: New to Ubuntu
---

### Post by pratap73 on 2019-04-01
```
sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdnav4 is already the newest version (6.0.0-1).
libdvdnav4 set to manually installed.
libdvdread4 is already the newest version (6.0.0-1).
libdvdread4 set to manually installed.
gstreamer1.0-plugins-bad is already the newest version (1.14.1-1ubuntu1~ubuntu18.04.1).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libdvd-pkg : Depends: build-essential but it is not going to be installed
              Depends: debhelper (>= 9) but it is not going to be installed
              Depends: dh-autoreconf but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by deadflowr on 2019-04-01
Run and post back the output from
```
sudo apt update
sudo apt install -f
```

Also, did you ever fix the issues from your other threads?
[https://ubuntuforums.org/showthread.php?t=2415250]("https://ubuntuforums.org/showthread.php?t=2415250")
[https://ubuntuforums.org/showthread.php?t=2415286]("https://ubuntuforums.org/showthread.php?t=2415286")
[https://ubuntuforums.org/showthread.php?t=2415311]("https://ubuntuforums.org/showthread.php?t=2415311")

---

### Post by pratap73 on 2019-04-01
still getting the same error!!

output of sudo apt install -f
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded
```



then tried this code
```
sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdnav4 is already the newest version (6.0.0-1).
libdvdnav4 set to manually installed.
libdvdread4 is already the newest version (6.0.0-1).
libdvdread4 set to manually installed.
gstreamer1.0-plugins-bad is already the newest version (1.14.1-1ubuntu1~ubuntu18.04.1).
gstreamer1.0-plugins-ugly is already the newest version (1.14.1-1~ubuntu18.04.1).
gstreamer1.0-plugins-ugly set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libdvd-pkg : Depends: build-essential but it is not going to be installed
              Depends: debhelper (>= 9) but it is not going to be installed
              Depends: dh-autoreconf but it is not going to be installed
E: Unable to correct problems, you have held broken packages
```

still getting the same error

---

### Post by deadflowr on 2019-04-01
Where is the sudo apt update output?

---

### Post by pratap73 on 2019-04-01
```
sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                        
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]      
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]    
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]
Fetched 341 kB in 4s (76.5 kB/s) 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
13 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:58
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:71
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:81
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:10 and /etc/apt/sources.list:63
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:20 and /etc/apt/sources.list:73
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:83
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (main/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (restricted/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (universe/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (multiverse/i18n/Translation-en_IN) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:38 and /etc/apt/sources.list:91
```

---

### Post by deadflowr on 2019-04-01
It seems you have multi-duplicate lines or entries in the sources.list file.
Please post the output from
```
cat /etc/apt/sources.list
```
[B]
Edit:[/B] Please use code tags when posting terminal output as code tags retain the proper formatting
See: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")
For a quick primer on code tags.

---

### Post by pratap73 on 2019-04-02
```

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb cdrom:[Ubuntu-Studio 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20151225)]/ xenial main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse

# Kali linux repositories | Added by Katoolin
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free
# Kali linux repositories | Added by Katoolin
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free
# Kali linux repositories | Added by Katoolin
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free

```

---

### Post by deadflowr on 2019-04-02
```
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb cdrom:[Ubuntu-Studio 16.04 LTS _Xenial Xerus_ - Alpha amd64 (20151225)]/ xenial main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
[b]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates main restricted[/b]

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[b]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates universe[/b]

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
[b]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates multiverse[/b]

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[b]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse[/b]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

[b]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse[/b]

# Kali linux repositories | Added by Katoolin
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free
# Kali linux repositories | Added by Katoolin
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free
# Kali linux repositories | Added by Katoolin
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free
```

I've Bolded duplicate entries.
I might have missed one or two, but the ones I selected are dupes so you can remove those lines.
I also bolded the source package repos (deb-src = source packag repositories) which you can enable or disable if you want.
They're not needed unless you plan on compiling software from apt source.

---

### Post by pratap73 on 2019-04-04
Thanks !!

---

