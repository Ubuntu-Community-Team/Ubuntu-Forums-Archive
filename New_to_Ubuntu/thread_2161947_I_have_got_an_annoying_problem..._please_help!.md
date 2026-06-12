---
title: "I have got an annoying problem... please help!"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by Ludowicus on 2013-07-12
This is my error!

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 172664 files and directories currently installed.)
Unpacking fglrx-experimental-12 (from .../fglrx-experimental-12_2%3a12.100-0ubuntu0.1_amd64.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: /usr/share/ati/fglrx-uninstall.sh: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent


[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the AMD driver
 is not installed, the AMD driver is only partially installed,
 or the current AMD driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).


dpkg: error processing /var/cache/apt/archives/fglrx-experimental-12_2%3a12.100-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx-experimental-12_2%3a12.100-0ubuntu0.1_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of fglrx-amdcccle-experimental-12:
 fglrx-amdcccle-experimental-12 depends on fglrx-experimental-12; however:
  Package fglrx-experimental-12 is not installed.
dpkg: error processing fglrx-amdcccle-experimental-12 (--configure):
 dependency problems - leaving unconfigured

```

At the moment I can't use my software cental for ubuntu at all, and i can't swtitch drivers or anything.
How do i deal with this?

---

### Post by uzumakifahim on 2013-07-12
What is the output of *sudo apt-get update *?

---

### Post by Ludowicus on 2013-07-13
Problem is solved. No worries!

---

### Post by dannyboy79 on 2013-07-13
can you "edit" you original post and from the drop down menu, mark it as solved please. thanks, glad you got it sorted out

---

