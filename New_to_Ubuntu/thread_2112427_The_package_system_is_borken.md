---
title: "The package system is borken"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by Twinbird on 2013-02-04
Hello,

When trying to update my system I get the following error:
> 
The package system is broken

Check if you are using third-party repositories. If so, disable them, because they are a common source of problems.
Furthermore, run the following command in a Terminal: apt-get install -f

Details:
The following packages have unmet dependencies:

mysql-server-5.5: PreDepends: mysql-common (>= 5.5.28-0ubuntu0.12.04.3) but 5.5.29-0ubuntu0.12.04.1 is installed
                  Depends: mysql-client-5.5 (>= 5.5.28-0ubuntu0.12.04.3) but 5.5.29-0ubuntu0.12.04.1 is installed
                  Depends: perl (>= 5.6) but 5.14.2-6ubuntu2.2 is installed
                  Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
                  Depends: upstart-job but it is a virtual package
                  Depends: mysql-server-core-5.5 (= 5.5.28-0ubuntu0.12.04.3) but it is not installed
I have spent hours searching for a solution but nothing has helped. I have tried the solutions at the below URLs but they did not help:
[http://askubuntu.com/questions/195882/the-package-system-is-broken](http://askubuntu.com/questions/195882/the-package-system-is-broken)
[http://askubuntu.com/questions/243904/how-to-fix-package-system-is-broken-after-upgrading-to-12-04](http://askubuntu.com/questions/243904/how-to-fix-package-system-is-broken-after-upgrading-to-12-04)

What can I do?

Thanks,

Twin

EDIT: BTW, I am trying to do this on an Ubuntu 12.04 LTS system which I currently have set up as a LAMP server - and right now I am trying to set up CAS authentication on it. I discovered this problem when I tried going through the following steps:
> 
**mod_auth_cas **

  mod_auth_cas is a pluggable authentication module for the Apache httpd server. 
 1.  Fetch the source and build: 
cd /tmp ; svn export [https://source.jasig.org/cas-clients/mod_auth_cas/trunk](https://source.jasig.org/cas-clients/mod_auth_cas/trunk)
cd /tmp/trunk ; /usr/sbin/apxs -c src/mod_auth_cas.c 


---

### Post by NikTh on 2013-02-04
Hi , 
try to use the [Package Manager troubleshooting procedure]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure")

Execute all commands from [step 5]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_5_List_of_Terminal_commands_to_execute") , one by one .. and post back here full results.

_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thank you.

---

### Post by Twinbird on 2013-02-05
Thanks for the reply NikTh. Below is the output from executing the commands from step 5:

```

rkomarom@rsg-pc102:/home/rkomaromi$ sudo grep -R proxy /etc/apt/*
[sudo] password for rkomarom: 
rkomarom@rsg-pc102:/home/rkomaromi$ sudo grep -R proxy /etc/apt/*
rkomarom@rsg-pc102:/home/rkomaromi$ echo $http_proxy

rkomarom@rsg-pc102:/home/rkomaromi$ echo $ftp_proxy

rkomarom@rsg-pc102:/home/rkomaromi$ grep proxy /etc/bash.bashrc
rkomarom@rsg-pc102:/home/rkomaromi$ sudo fuser -vvv /var/lib/dpkg/lock
rkomarom@rsg-pc102:/home/rkomaromi$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
rkomarom@rsg-pc102:/home/rkomaromi$ uname -a
Linux rsg-pc102.cs.uwaterloo.ca 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
rkomarom@rsg-pc102:/home/rkomaromi$ sudo rm /var/lib/apt/lists/lock 
rkomarom@rsg-pc102:/home/rkomaromi$ sudo rm /var/lib/dpkg/lock
rkomarom@rsg-pc102:/home/rkomaromi$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
^Crkomarom@rsg-pc102:/home/rkomaromi$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
rkomarom@rsg-pc102:/home/rkomaromi$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
rkomarom@rsg-pc102:/home/rkomaromi$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status  ||  sudo cp /var/backups/apt.extended_states.0 /var/lib/dpkg/status
rkomarom@rsg-pc102:/home/rkomaromi$ sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad
rkomarom@rsg-pc102:/home/rkomaromi$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
rkomarom@rsg-pc102:/home/rkomaromi$ sudo rm -rf /var/lib/dpkg/updates/*
rkomarom@rsg-pc102:/home/rkomaromi$ sudo rm -rf /var/lib/apt/lists
rkomarom@rsg-pc102:/home/rkomaromi$ sudo rm /var/cache/apt/*.bin
rkomarom@rsg-pc102:/home/rkomaromi$ sudo mkdir /var/lib/apt/lists
rkomarom@rsg-pc102:/home/rkomaromi$ sudo mkdir /var/lib/apt/lists/partial
rkomarom@rsg-pc102:/home/rkomaromi$ LANG=C;sudo apt-get clean
rkomarom@rsg-pc102:/home/rkomaromi$ LANG=C;sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rkomarom@rsg-pc102:/home/rkomaromi$ LANG=C;sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-server-5.5 : Depends: mysql-server-core-5.5 (= 5.5.28-0ubuntu0.12.04.3) but it is not installable
E: Unmet dependencies. Try using -f.
rkomarom@rsg-pc102:/home/rkomaromi$ LANG=C;sudo apt-get update -o APT::Cache-Limit=100000000
Ign http://archive.ubuntu.com precise InRelease
Ign http://security.ubuntu.com precise-security InRelease
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:3 http://archive.ubuntu.com precise Release [49.6 kB]  
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:5 http://archive.ubuntu.com precise/restricted amd64 Packages [8452 B]
Get:6 http://security.ubuntu.com precise-security/main amd64 Packages [225 kB]
Get:7 http://archive.ubuntu.com precise/universe amd64 Packages [4786 kB]
Get:8 http://security.ubuntu.com precise-security/restricted amd64 Packages [3969 B]
Get:9 http://security.ubuntu.com precise-security/universe amd64 Packages [62.7 kB]
Get:10 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2184 B]     
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [234 kB]            
Get:12 http://security.ubuntu.com precise-security/restricted i386 Packages [3968 B]       
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [64.2 kB]    
Get:14 http://security.ubuntu.com precise-security/multiverse i386 Packages [2366 B]       
Get:15 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]             
Get:16 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]       
Get:17 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:18 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:19 http://security.ubuntu.com precise-security/main Translation-en [110 kB]  
Get:20 http://security.ubuntu.com precise-security/multiverse Translation-en [995 B]
Get:21 http://security.ubuntu.com precise-security/restricted Translation-en [978 B]
Get:22 http://security.ubuntu.com precise-security/universe Translation-en [38.4 kB]   
Get:23 http://archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]            
Get:24 http://archive.ubuntu.com precise/main amd64 Packages [1273 kB]
Get:25 http://archive.ubuntu.com precise/restricted i386 Packages [8431 B]
Get:26 http://archive.ubuntu.com precise/universe i386 Packages [4796 kB]
Get:27 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]
Get:28 http://archive.ubuntu.com precise/main i386 Packages [1274 kB]
Get:29 http://archive.ubuntu.com precise/main TranslationIndex [3706 B]
Get:30 http://archive.ubuntu.com precise/multiverse TranslationIndex [2676 B]
Get:31 http://archive.ubuntu.com precise/restricted TranslationIndex [2596 B]
Get:32 http://archive.ubuntu.com precise/universe TranslationIndex [2922 B]
Get:33 http://archive.ubuntu.com precise/main Translation-en [726 kB]
Get:34 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:35 http://archive.ubuntu.com precise/restricted Translation-en [2395 B]
Get:36 http://archive.ubuntu.com precise/universe Translation-en [3341 kB]
Fetched 17.4 MB in 10s (1638 kB/s)                                                          
Reading package lists... Done
rkomarom@rsg-pc102:/home/rkomaromi$ sudo dpkg --configure -a
rkomarom@rsg-pc102:/home/rkomaromi$ sudo dpkg --clear-avail
rkomarom@rsg-pc102:/home/rkomaromi$ LANG=C;sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-25 linux-headers-3.2.0-27 linux-headers-3.2.0-34
  linux-headers-3.2.0-34-generic libocsync-plugin-smb libocsync-plugin-sftp wine-gecko1.8
  wine-gecko1.8:i386 linux-headers-3.2.0-27-generic linux-headers-3.2.0-25-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.5 mysql-server-core-5.5
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server-core-5.5
The following packages will be upgraded:
  mysql-server-5.5
1 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 14.9 MB of archives.
After this operation, 20.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main mysql-server-5.5 amd64 5.5.29-0ubuntu0.12.04.1 [8832 kB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/main mysql-server-core-5.5 amd64 5.5.29-0ubuntu0.12.04.1 [6055 kB]
Fetched 14.9 MB in 1s (12.9 MB/s)           
Selecting previously unselected package mysql-server-core-5.5.
(Reading database ... 498160 files and directories currently installed.)
Unpacking mysql-server-core-5.5 (from .../mysql-server-core-5.5_5.5.29-0ubuntu0.12.04.1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mysql-server-core-5.5 (5.5.29-0ubuntu0.12.04.1) ...
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.28-0ubuntu0.12.04.3); however:
  Version of mysql-server-core-5.5 on system is 5.5.29-0ubuntu0.12.04.1.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
             Errors were encountered while processing:
 mysql-server-5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)
rkomarom@rsg-pc102:/home/rkomaromi$ LANG=C;sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-server-5.5 : Depends: mysql-server-core-5.5 (= 5.5.28-0ubuntu0.12.04.3) but 5.5.29-0ubuntu0.12.04.1 is installed
E: Unmet dependencies. Try using -f.
rkomarom@rsg-pc102:/home/rkomaromi$ LANG=C;sudo apt-get update -o APT::Cache-Limit=100000000 && sudo apt-get dist-upgrade
Ign http://security.ubuntu.com precise-security InRelease
Ign http://archive.ubuntu.com precise InRelease
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://archive.ubuntu.com precise Release
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://archive.ubuntu.com precise/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe amd64 Packages
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise/main amd64 Packages
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/universe i386 Packages
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-server-5.5 : Depends: mysql-server-core-5.5 (= 5.5.28-0ubuntu0.12.04.3) but 5.5.29-0ubuntu0.12.04.1 is installed
E: Unmet dependencies. Try using -f.
rkomarom@rsg-pc102:/home/rkomaromi$ find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     2    
     3    # newer versions of the distribution.
     4    # deb http://mirror.cs.uwaterloo.ca/ubuntu/ precise main restricted
     5    # deb-src http://mirror.cs.uwaterloo.ca/ubuntu/ precise main restricted
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    # deb http://mirror.cs.uwaterloo.ca/ubuntu/ precise-updates main restricted
    10    # deb-src http://mirror.cs.uwaterloo.ca/ubuntu/ precise-updates main restricted
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    # deb http://mirror.cs.uwaterloo.ca/ubuntu/ precise universe
    16    # deb-src http://mirror.cs.uwaterloo.ca/ubuntu/ precise universe
    17    # deb http://mirror.cs.uwaterloo.ca/ubuntu/ precise-updates universe
    18    # deb-src http://mirror.cs.uwaterloo.ca/ubuntu/ precise-updates universe
    19    
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21    ## team, and may not be under a free licence. Please satisfy yourself as to 
    22    ## your rights to use the software. Also, please note that software in 
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    # deb http://mirror.cs.uwaterloo.ca/ubuntu/ precise multiverse
    26    # deb-src http://mirror.cs.uwaterloo.ca/ubuntu/ precise multiverse
    27    # deb http://mirror.cs.uwaterloo.ca/ubuntu/ precise-updates multiverse
    28    # deb-src http://mirror.cs.uwaterloo.ca/ubuntu/ precise-updates multiverse
    29    
    30    ## N.B. software from this repository may not have been tested as
    31    ## extensively as that contained in the main release, although it includes
    32    ## newer versions of some applications which may provide useful features.
    33    ## Also, please note that software in backports WILL NOT receive any review
    34    ## or updates from the Ubuntu security team.
    35    # deb http://mirror.cs.uwaterloo.ca/ubuntu/ precise-backports main restricted universe multiverse
    36    # deb-src http://mirror.cs.uwaterloo.ca/ubuntu/ precise-backports main restricted universe multiverse
    37    
    38    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    39    deb http://security.ubuntu.com/ubuntu precise-security universe
    40    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    41    
    42    ## Uncomment the following two lines to add software from Canonical's
    43    ## 'partner' repository.
    44    ## This software is not part of Ubuntu, but is offered by Canonical and the
    45    ## respective vendors as a service to Ubuntu users.
    46    # deb http://archive.canonical.com/ubuntu precise partner
    47    # deb-src http://archive.canonical.com/ubuntu precise partner
    48    
    49    ## Uncomment the following two lines to add software from Ubuntu's
    50    ## 'extras' repository.
    51    ## This software is not part of Ubuntu, but is offered by third-party
    52    ## developers who want to ship their latest software.
    53    # deb http://extras.ubuntu.com/ubuntu precise main
    54    # deb-src http://extras.ubuntu.com/ubuntu precise main
    55    # deb http://archive.canonical.com/ precise partner
    56    # deb-src http://archive.canonical.com/ precise partner
    57    deb http://archive.ubuntu.com/ubuntu precise restricted universe multiverse main

/etc/apt/sources.list.d/mozillateam-firefox-stable-precise.list

     1    # deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main
     2    # deb-src http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main

/etc/apt/sources.list.d/mozillateam-thunderbird-stable-precise.list

     1    # deb http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu precise main
     2    # deb-src http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu precise main

/etc/apt/sources.list.d/jonoomph-openshot-edge-precise.list

     1    # deb http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu precise main
     2    # deb-src http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu precise main

/etc/apt/sources.list.d/audacity-team-daily-precise.list

     1    # deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main
     2    # deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main

/etc/apt/sources.list.d/owncloud-client.list

     1    # deb http://download.opensuse.org/repositories/isv:ownCloud:devel/xUbuntu_12.04/ /
     2    # deb http://download.opensuse.org/repositories/isv:ownCloud:devel/xUbuntu_12.04/ /
     3    # deb http://download.opensuse.org/repositories/isv:ownCloud:devel/xUbuntu_12.04/ /

/etc/apt/sources.list.d/medibuntu.list

     1    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
     2    # deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
     3    # deb-src http://packages.medibuntu.org/ precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"

/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list

     1    # deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
     2    # deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

/etc/apt/sources.list.d/stebbins-handbrake-snapshots-precise.list

     1    # deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main
     2    # deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main

/etc/apt/sources.list.d/team-xbmc-ppa-precise.list

     1    # deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main
     2    # deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu precise main
rkomarom@rsg-pc102:/home/rkomaromi$

```

---

### Post by furything on 2013-02-05
How were trying to install mysql?
Did you do this through the package manager/synaptic or did you download a package e.g. .deb and try and install it that way?

Personally I would remove the offending package
```
sudo dpkg --force-all -P mysql-server-5.5
```make sure all ok 
```
sudo apt-get update && sudo apt-get upgrade
```Then use package mgr to load correct version

---

### Post by Twinbird on 2013-02-05
I installed it using the following command in the Terminal:
```

sudo apt-get install mysql-server mysql-client

```

Running your first command I get the following output:
```

rkomarom@rsg-pc102:/home/rkomaromi$ sudo dpkg --force-all - P mysql-server-5.5
[sudo] password for rkomarom: 
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
rkomarom@rsg-pc102:/home/rkomaromi$ 

```

---

### Post by raja.genupula on 2013-02-05
you mean your issue got solved ?

---

### Post by Twinbird on 2013-02-05
No, not solved. I replied to [furything]("http://ubuntuforums.org/member.php?u=1776458")'s original question. Then I saw the edit... maybe I should just reinstall Ubuntu? :(

---

### Post by raja.genupula on 2013-02-05
you'd better Quote the message , so it will reach as the reply of correct post. 

So you can use , [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) to regenerate your source list and re update the cache.

so that its gonna be fine.

give a try.

---

### Post by furything on 2013-02-05
Sorry guys the - P should be -P
my bad 
Try again without the space

Edited code above

---

### Post by Twinbird on 2013-02-05
> **furything said:**
> Sorry guys the - P should be -P
my bad 
Try again without the space

Edited code above
Thanks. I typed it corrently and now I get the following output:
> 
rkomarom@rsg-pc102:/home/rkomaromi$ sudo dpkg --force-all -P mysql-server-5.5
[sudo] password for rkomarom: 
(Reading database ... 498245 files and directories currently installed.)
Removing mysql-server-5.5 ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S99mysql
dpkg: error processing mysql-server-5.5 (--purge):
 subprocess installed pre-removal script returned error exit status 102
invoke-rc.d: dangling symlink: /etc/rc2.d/S99mysql
invoke-rc.d: dangling symlink: /etc/rc2.d/S99mysql
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 102
Errors were encountered while processing:
 mysql-server-5.5
rkomarom@rsg-pc102:/home/rkomaromi$ 

> **raja.genupula said:**
> you'd better Quote the message , so it will reach as the reply of correct post. 

So you can use , [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) to regenerate your source list and re update the cache.

so that its gonna be fine.

give a try.
I tried this and it did not seem to help either :(

---

### Post by furything on 2013-02-06
Ok lets try deselecting the myslq so we can start from scratch
```
sudo dpkg -r mysql-server-5.5
sudo dpkg -r  mysql-server-core-5.5
```This should unmark it for installation

then ```
sudo apt-get update && sudo apt-get upgrade
```At this point has the error gone away?
You should see only today's updates and nothing about my sql.

Now using the package manager not terminal and apt-get try and find mysql again and install it.

I  note form your earlier logs that you have precise 12.04.02 but the mysql wants 12.04.03

---

### Post by Twinbird on 2013-02-07
The error is now gone. Things seem to be working fine now. Thanks furything, and everyone else!

I also used information from the following post to help me:
[http://ubuntuforums.org/showthread.php?t=240699](http://ubuntuforums.org/showthread.php?t=240699)

I now have another thing I need help with, but that is for a new thread.

---

