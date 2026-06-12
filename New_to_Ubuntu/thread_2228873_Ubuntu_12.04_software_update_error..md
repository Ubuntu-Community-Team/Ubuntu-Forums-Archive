---
title: "Ubuntu 12.04 software update error."
date: 2014-06-10
forum: New to Ubuntu
---

### Post by facosta on 2014-06-10
Hello

I am running Ubuntu 12.04 and keep getting software update errors. Attached are screenshots of the error along with details.
I am also adding the System Log below at the time the error occurs:

06/10/14 12:34:53 AM    ubuntu    AptDaemon.PackageKit    INFO: Get updates()
06/10/14 12:34:54 AM    ubuntu    AptDaemon.Worker    INFO: Finished transaction /org/debian/apt/transaction/cd560749cb60411f8a40f54764fb6c62
06/10/14 12:35:31 AM    ubuntu    kernel    [  224.782558] sda1: WRITE SAME failed. Manually zeroing.
06/10/14 12:37:18 AM    ubuntu    anacron[1227]    Job `cron.daily' started
06/10/14 12:37:18 AM    ubuntu    anacron[3201]    Updated timestamp for job `cron.daily' to 2014-06-10
06/10/14 12:37:22 AM    ubuntu    postfix/pickup[1978]    A32D441226: uid=0 from=<root>
06/10/14 12:37:22 AM    ubuntu    postfix/cleanup[4489]    A32D441226: message-id=<20140610073722.A32D441226@ubuntu>
06/10/14 12:37:22 AM    ubuntu    postfix/qmgr[1979]    A32D441226: from=<root@ubuntu>, size=1446, nrcpt=1 (queue active)
06/10/14 12:37:23 AM    ubuntu    postfix/local[4499]    A32D441226: to=<root@ubuntu>, orig_to=<root>, relay=local, delay=0.76, delays=0.5/0.16/0/0.11, dsn=2.0.0, status=sent (delivered to mailbox)
06/10/14 12:37:23 AM    ubuntu    postfix/qmgr[1979]    A32D441226: removed
06/10/14 12:40:04 AM    ubuntu    AptDaemon    INFO: Quitting due to inactivity
06/10/14 12:40:04 AM    ubuntu    AptDaemon    INFO: Quitting was requested

Is there a way to resolve this issue? Thanks.

---

### Post by facosta on 2014-06-10
I have tried this: 'sudo update-manager -d' but fails.

facosta@ubuntu:~$ sudo update-manager -d
[sudo] password for facosta: 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 33, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 71, in <module>
    from Core.UpdateList import UpdateList
ImportError: cannot import name UpdateList
facosta@ubuntu:~$

---

### Post by rahul4557 on 2014-06-10
Safest way to go around would be..
Press CTRL+ALT+F1
type
> sudo apt-get update
 after that
> sudo apt-get upgrade

system will be updated from terminal.
after that restart the system
> sudo init 6

---

### Post by facosta on 2014-06-10
Thanks Rahul4557

I wil try the sudo commands. So far no update errors. I did find a helpful web page for Debugging
the Update Manager. Here is the link [https://wiki.ubuntu.com/DebuggingUpdateManager](https://wiki.ubuntu.com/DebuggingUpdateManager). Synaptic
Package Manager also is a good work-around. Thanks.

---

### Post by facosta on 2014-06-13
Here is my crash report for the new update error:


ProblemType: Crash
CrashCounter: 1
Date: Thu Jun 12 23:22:39 2014
ExecutablePath: /usr/bin/update-manager
ExecutableTimestamp: 1397254302
InterpreterPath: /usr/bin/python2.7
ProcCmdline: /usr/bin/python /usr/bin/update-manager
ProcCwd: /
ProcEnviron:
 SHELL=/bin/bash
 PATH=(custom, no user)
 LANG=en_US.UTF-8
ProcMaps:
 00400000-00672000 r-xp 00000000 08:01 395244                             /usr/bin/python2.7
 00871000-00872000 r--p 00271000 08:01 395244                             /usr/bin/python2.7
 00872000-008db000 rw-p 00272000 08:01 395244                             /usr/bin/python2.7

PythonArgs: ['/usr/bin/update-manager']
Traceback:
 Traceback (most recent call last):
   File "/usr/bin/update-manager", line 33, in <module>
     from UpdateManager.UpdateManager import UpdateManager
   File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 71, in <module>
     from Core.UpdateList import UpdateList
 ImportError: cannot import name UpdateList

InstallationMedia: Ubuntu 12.04.3 LTS "Precise Pangolin" - Release amd64 (20130820.1)
MarkForUpload: True
Package: update-manager 1:0.156.14.13
PackageArchitecture: all
ProcVersionSignature: Ubuntu 3.8.0-42.62~precise1-generic 3.8.13.23
SourcePackage: update-manager
Tags:  precise running-unity
Title: update-manager crashed with ImportError in /usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py: cannot import name UpdateList
Uname: Linux 3.8.0-42-generic x86_64
UpgradeStatus: No upgrade log present (probably fresh install)

---

### Post by facosta on 2014-07-14
Ubuntu 12.04 update manager error continues:

1.```
sudo apt-get update

```

2.```
sudo apt-get dist-upgrade
```

Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
update-manager : Depends: update-manager-core (= 1:0.156.14.15) but 1:0.156.14.13 is installed
update-notifier-common : Depends: update-manager-core (>= 1:0.156.14.15) but 1:0.156.14.13 is installed
E: Unmet dependencies. Try using -f.

3.```
sudo apt-get -f install
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  update-notifier-common libgpds0 language-pack-kde-en kde-l10n-engb patch
  language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  update-manager-core
The following packages will be upgraded:
  update-manager-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 185 kB of archives.
After this operation, 28.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main update-manager-core amd64 1:0.156.14.15 [185 kB]
Fetched 185 kB in 0s (211 kB/s)              
Setting up update-manager-core (1:0.156.14.13) ...
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeController.py'
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/DistUpgrade/apt_btrfs_snapshot.py'
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeViewKDE.py'
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/DistUpgrade/apt-autoinst-fixup.py'
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/UpdateManager/Core/AlertWatcher.py'
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/UpdateManager/Core/UpdateList.py'
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/UpdateManager/Core/__init__.py'
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/UpdateManager/Core/MetaRelease.py'
[Errno 21] Is a directory: '/usr/lib/python2.7/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py'
dpkg: error processing update-manager-core (--configure):
 subprocess installed post-installation script returned error exit status 101
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on update-manager-core (>= 1:0.156.14.15); however:
  Version of update-manager-core on system is 1:0.156.14.13.
dpkg: error processing update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.156.14.15); however:
  Version of update-manager-core on system is 1:0.156.14.13.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 update-manager-core
 update-notifier-common
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is there a way to resolve this issue? Update Manager in Dash does not work. Dash is unstable.

---

### Post by facosta on 2014-07-14
I also have tried package recovery in GRUB and tried the sudo commands in root.
Same problem.

---

### Post by bapoumba on 2014-07-14
Strange that your installed version is lower than the candidate and an upgrade or dist-upgrade does not pull it through.
Please post the output to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by facosta on 2014-07-14
Hi bapoumba

Here are the results:



```

facosta@ubuntu:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted
     5    
     6    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     7    # newer versions of the distribution.
     8    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     9    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    14    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    20    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    21    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    22    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    30    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    31    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    32    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    40    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    41    
    42    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    43    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    44    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    45    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    46    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    47    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    54    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    59    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
```


```
facosta@ubuntu:~$ ls -la /etc/apt/sources.list.d
total 12
drwxr-xr-x 2 root root 4096 Jun  4 20:44 .
drwxr-xr-x 6 root root 4096 Jun 20 22:04 ..
-rw-r--r-- 1 root root  160 Jun  4 20:44 private-ppa.launchpad.net_commercial-ppa-uploaders_fragment_ubuntu.list
```

```
facosta@ubuntu:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_fragment_ubuntu.list <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/fragment/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/fragment/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
```

---

### Post by bapoumba on 2014-07-14
I cannot connect to [https://private-ppa.launchpad.net/co...ragment/ubuntu](https://private-ppa.launchpad.net/co...ragment/ubuntu), it requires authentication. What did you install from there ?

---

### Post by facosta on 2014-07-14
I did not install anything from launchpad.net, I did use Synaptic Package Downloader
to install updates but after that Dash became unstable, Synaptic Package Download
does not work and now just a simple update install from the terminal is not happy.

---

### Post by facosta on 2014-07-14
I did not download anything from launchpad.net. I did use synaptic package downloader
for updates. After that Dash,Synaptic Package and Update Manager became very unstable
and would lockup.

---

### Post by bapoumba on 2014-07-14
Hmm, it may have pulled upgrades from there. The best way is to install ppa-purge ([https://launchpad.net/ppa-purge](https://launchpad.net/ppa-purge)) and run it to revert all packages to their regular version.
If your package managers are not happy, we may have to do it some other way.

For now, please run :
```
sudo apt-get install ppa-purge
```
Or try form synaptic or other way.

If this does work (I have reservations), please run :
```
sudo ppa-purge ppa:commercial-ppa-uploaders/fragment
sudo apt-get update
sudo apt-get upgrade
```

If this does not work, we'll work it out from there :)

---

### Post by facosta on 2014-07-14
Entered command and same error.

```
sudo apt-get install ppa-purge
```


facosta@ubuntu:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
ppa-purge : Depends: aptitude but it is not going to be installed
update-manager : Depends: update-manager-core (= 1:0.156.14.15) but 1:0.156.14.13 is to be installed
update-notifier-common : Depends: update-manager-core (>= 1:0.156.14.15) but 1:0.156.14.13 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by bapoumba on 2014-07-14
OK, lets move to this :
```
sudo apt-add-repository --remove ppa:commercial-ppa-uploaders/fragment
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by facosta on 2014-07-14
Sudo command ran with result below:

facosta@ubuntu:~$ sudo apt-add-repository --remove ppa:commercial-ppa-uploaders/fragment
Traceback (most recent call last):
File "/usr/bin/apt-add-repository", line 8, in <module>
from softwareproperties.SoftwareProperties import SoftwareProperties, expand_shortcut_line
File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 25, in <module>
import apt
File "/usr/lib/python2.7/dist-packages/apt/__init__.py", line 21, in <module>import apt_pkg
ImportError: No module named apt_pkg

---

### Post by facosta on 2014-07-14
I went back to a previous linux version though GRUB at startup and loaded linux-image-3.8.0-38-generic.
Dash started working and so did Synaptic Package Downloader. I was able to remove update-manager
1:0.156.14.15 and update-notifier-common 0.119ubuntu8.7 packages. Dash is stable. The only question
is if I update, how do I prevent these frequent update error with Ubuntu 12.04 LTS software?

---

### Post by facosta on 2014-07-14
Here is a snapshot of the packages needed to be removed:
Another question; Is it safe to continue to do updates for ubuntu 12.04 LTS?

[ATTACH=CONFIG]254722[/ATTACH]

---

### Post by bapoumba on 2014-07-15
If you have access to a working synaptic now, please try to install ppa-purge and remove your ppa. To me, that is the first thing to do.

If you cannot install ppa-purge, remove the ppa from synaptic sources, or move /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_fragment_ubuntu.list to your Desktop (you can delete it later), so that /etc/apt/sources.list.d/ is empty. Then try the update/upgrade again.

12.04 LTS is still maintained, so yes you should apply updates/upgrades as they come in. The problem being some updates you applied brought in packages having conflicting versions with the standard distribution ones. At least that is my way of seeing it :)

---

### Post by facosta on 2014-07-15
Thanks for the help. It worked. I removed PPA from using synaptic. 
No more conflicts with update manager!
 :guitar:

---

### Post by bapoumba on 2014-07-15
Glad to see you got it to work :)

---

