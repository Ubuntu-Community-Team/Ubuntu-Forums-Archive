---
title: "Error encountered while processing"
date: 2019-06-19
forum: New to Ubuntu
---

### Post by mas192 on 2019-06-19
Dear forum member,

I am having this error that is affecting my installations, basically when I execute ```
sudo apt-get update && sudo apt-get upgrade
```

I get this error
```
"The following packages were automatically installed and are no longer required:  libpython-stdlib python python-minimal python2.7 python2.7-minimal
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  mysql-connector-python
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,362 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 191687 files and directories currently installed.)
Removing mysql-connector-python (8.0.16-1ubuntu18.04) ...
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'distutils.sysconfig'
dpkg: error processing package mysql-connector-python (--remove):
 installed mysql-connector-python package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 mysql-connector-python
E: Sub-process /usr/bin/dpkg returned an error code (1)"
```

Please help me fix this
Thank so much

---

### Post by Bashing-om on 2019-06-19
mas192; Yukkie -

The package " mysql-connector-python" is not in my mirror archive. So what are we working with ?

What release is this ?
```

lsb_release -a

```
and what are the sources ?
```

apt policy libpython-stdlib python python-minimal python2.7 python2.7-minimal mysql-connector-python

```

A PPA ? the code will tell

[INDENT]use the source, Luke !
[/INDENT]

---

### Post by mas192 on 2019-06-19
Yukkie thanks so much here is the release info

```
"No LSB modules are available.Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic"
```

Also its seems everything but the mysql-connector-python is there, please check below
"
```
libpython-stdlib:
  Installed: 2.7.15~rc1-1
  Candidate: 2.7.15~rc1-1
  Version table:
 *** 2.7.15~rc1-1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status
python:
  Installed: 2.7.15~rc1-1
  Candidate: 2.7.15~rc1-1
  Version table:
 *** 2.7.15~rc1-1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status
python-minimal:
  Installed: 2.7.15~rc1-1
  Candidate: 2.7.15~rc1-1
  Version table:
 *** 2.7.15~rc1-1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status
python2.7:
  Installed: 2.7.15-4ubuntu4~18.04
  Candidate: 2.7.15-4ubuntu4~18.04
  Version table:
 *** 2.7.15-4ubuntu4~18.04 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.7.15~rc1-1ubuntu0.1 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
     2.7.15~rc1-1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
python2.7-minimal:
  Installed: 2.7.15-4ubuntu4~18.04
  Candidate: 2.7.15-4ubuntu4~18.04
  Version table:
 *** 2.7.15-4ubuntu4~18.04 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.7.15~rc1-1ubuntu0.1 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
     2.7.15~rc1-1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
python:
  Installed: 2.7.15~rc1-1
  Candidate: 2.7.15~rc1-1
  Version table:
 *** 2.7.15~rc1-1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status
N: Unable to locate package mysql-connector"
```

What do you think are my next steps!!!

Cheers,
mas192

---

### Post by Bashing-om on 2019-06-20
mas192; Hymmm ...

Is this a "MySQL APT Repository" issue ?
Seems now that some MySQL packaging has been moved out of our archives.
And - we are out of the range of my experience. All I can do now is poke and stroke, seeing what we can learn.

Please post back - Using code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Please !
the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
dpkg -l | grep mysql

```

see here if we can find out why apt has no handle on the installed mysql-connector-python package.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Impavidus on 2019-06-20
> **mas192 said:**
> 
Also its seems everything but the mysql-connector-python is there, please check below
```
...
N: Unable to locate package mysql-connector"
```

What do you think are my next steps!!!

Cheers,
mas192

Something went wrong there while copying the command. It lists python twice, skips mysql-connector-python and reports mysql-connector as not available. Try again:```
apt policy mysql-connector-python
```
I'd also like to know why apt-get upgrade wants to remove a package and what's the package that's neither fully installed nor removed.```
dpkg --list | grep -v '^ii\|^rc'
```That will list all packages with a status other than fully removed, remaining config or installed. Maybe the partially installed package has to be reinstalled to get the post-removal script for mysql-connector-python working again. Try```
apt show mysql-connector-python
```to see the dependencies.

---

### Post by mas192 on 2019-06-20
Inquiring minds will always find it

Please let me know what you think, also i could order in beer for your troubles you are my saviour
```
[COLOR=#000000][FONT=&amp]cat -n /etc/apt/sources.list
[/FONT][/COLOR]#output:
1    # deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://ca.archive.ubuntu.com/ubuntu/ bionic main restricted
     6    # deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://ca.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
    11    # deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://ca.archive.ubuntu.com/ubuntu/ bionic universe
    17    # deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic universe
    18    deb http://ca.archive.ubuntu.com/ubuntu/ bionic-updates universe
    19    # deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://ca.archive.ubuntu.com/ubuntu/ bionic multiverse
    27    # deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic multiverse
    28    deb http://ca.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
    29    # deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://ca.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
    37    # deb-src http://ca.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
    38    
    39    ## Uncomment the following two lines to add software from Canonical's
    40    ## 'partner' repository.
    41    ## This software is not part of Ubuntu, but is offered by Canonical and the
    42    ## respective vendors as a service to Ubuntu users.
    43    # deb http://archive.canonical.com/ubuntu bionic partner
    44    # deb-src http://archive.canonical.com/ubuntu bionic partner
    45    
    46    deb http://security.ubuntu.com/ubuntu bionic-security main restricted
    47    # deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
    48    deb http://security.ubuntu.com/ubuntu bionic-security universe
    49    # deb-src http://security.ubuntu.com/ubuntu bionic-security universe
    50    deb http://security.ubuntu.com/ubuntu bionic-security multiverse
    51    # deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```

```
tail -v -n +1 /etc/apt/sources.list.d/*
#output:
==> /etc/apt/sources.list.d/alessandro-strada-ubuntu-ppa-bionic.list <==


==> /etc/apt/sources.list.d/alessandro-strada-ubuntu-ppa-bionic.list.save <==


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-bionic.list <==
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main


==> /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-bionic.list.save <==
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main


==> /etc/apt/sources.list.d/mysql.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out entries below, but any other modifications may be lost.
# Use command 'dpkg-reconfigure mysql-apt-config' as root for modifications.
deb http://repo.mysql.com/apt/ubuntu/ bionic mysql-apt-config
deb http://repo.mysql.com/apt/ubuntu/ bionic mysql-8.0
deb http://repo.mysql.com/apt/ubuntu/ bionic mysql-tools
# deb http://repo.mysql.com/apt/ubuntu/ bionic mysql-tools-preview
deb-src http://repo.mysql.com/apt/ubuntu/ bionic mysql-8.0


==> /etc/apt/sources.list.d/mysql.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out entries below, but any other modifications may be lost.
# Use command 'dpkg-reconfigure mysql-apt-config' as root for modifications.
deb http://repo.mysql.com/apt/ubuntu/ bionic mysql-apt-config
deb http://repo.mysql.com/apt/ubuntu/ bionic mysql-8.0
deb http://repo.mysql.com/apt/ubuntu/ bionic mysql-tools
# deb http://repo.mysql.com/apt/ubuntu/ bionic mysql-tools-preview
deb-src http://repo.mysql.com/apt/ubuntu/ bionic mysql-8.0



```

```
dpkg -l | grep mysql
#ouput:
ii  mysql-apt-config                           0.8.13-1                                     all          Auto configuration for MySQL APT Repo.
ii  mysql-client                               8.0.16-2ubuntu18.04                          amd64        MySQL Client meta package depending on latest version
ii  mysql-common                               8.0.16-2ubuntu18.04                          amd64        Common files shared between packages
ii  mysql-community-client                     8.0.16-2ubuntu18.04                          amd64        MySQL Client
ii  mysql-community-client-core                8.0.16-2ubuntu18.04                          amd64        MySQL Client Core Binaries
ii  mysql-community-server                     8.0.16-2ubuntu18.04                          amd64        MySQL Server
ii  mysql-community-server-core                8.0.16-2ubuntu18.04                          amd64        MySQL Server Core Binaires
iH  mysql-connector-python                     8.0.16-1ubuntu18.04                          all          MySQL database driver written in pure Python
ii  mysql-server                               8.0.16-2ubuntu18.04                          amd64        MySQL Server meta package depending on latest version
rc  mysql-utilities                            1.6.5-1ubuntu16.10                           all          Collection of scripts for managing MySQL servers
ii  mysql-workbench-community                  8.0.16-1ubuntu18.04                          amd64        MySQL Workbench
ii  php-mysql                                  1:7.2+60ubuntu1                              all          MySQL module for PHP [default]
ii  php7.2-mysql                               7.2.19-0ubuntu0.18.04.1                      amd64        MySQL module for PHP
```

---

### Post by Bashing-om on 2019-06-20
mas192; Well well ..

what we know:
External PPA !
> 
/etc/apt/sources.list.d/mysql.list >> iH  mysql-connector-python    8.0.16-1ubuntu18.04


Now we look at our archive:
```

sysop@x1804mini:~$ apt show mysql-connector-python
N: Unable to locate package mysql-connector-python
N: Unable to locate package mysql-connector-python
E: No packages found

```
And it is not there, so we conclude it comes from that PPA.

So now the question is " How to invoke the re-install from that PPA".
And that I must go alook'n to find out.

When I know more I be back :)
[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by mas192 on 2019-06-20
Yay that is so promising thanks so much!!!!

---

### Post by Bashing-om on 2019-06-20
mas192; welp -

My -Fu is failing me. Not making a lot of headway.

However -
For think'n purposes, what returns:
```

sudo systemctl status mysql

```
As I continue to dither how to proceed.
( a license issue prompted the removal of the MySql from our archives) we have to find a way to deal with the residue.

[INDENT]looking, but I do not see
[/INDENT]

---

### Post by Bashing-om on 2019-06-20
mas192; Hey !

I think I got a handle on it !

Yup - MySQL now provides "mysql-connector-python"
open:
[https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#apt-repo-remove](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#apt-repo-remove)
see table one.

Now we need to purge the present mysql-connector-python - if we can, do:
```

sudo apt --force-yes remove mysql-connector-python

```

*If* that runs we next make the new source available as per the tutorial:
edit the file " /etc/apt/sources.list.d/mysql.list " and add:
```

deb http://repo.mysql.com/apt/ubuntu/ bionoc connector-python-2.7

```
where I "think"  connector-python-2.7 is the correct name of the repo we want.
Update the database:
```

sudo apt update
sudo apt upgrade

```

and now the finale e
```

sudo apt install mysql-connector-python

```

[INDENT][INDENT]all finer than a frog's hair ?
[/INDENT][/INDENT]

---

### Post by mas192 on 2019-06-21
Hi  Bashing-om

This is promising but I get the same error for

```
sudo apt --force-yes remove mysql-connector-python#errorbelow
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-connector-python
0 upgraded, 0 newly installed, 1 to remove and 30 not upgraded.
1 not fully installed or removed.
After this operation, 1,362 kB disk space will be freed.
W: --force-yes is deprecated, use one of the options starting with --allow instead.
Do you want to continue? [Y/n] Y
(Reading database ... 191577 files and directories currently installed.)
Removing mysql-connector-python (8.0.16-1ubuntu18.04) ...
/var/lib/dpkg/info/mysql-connector-python.postrm: 1: /var/lib/dpkg/info/mysql-connector-python.postrm: pyversions: not found
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'distutils.sysconfig'
dpkg: error processing package mysql-connector-python (--remove):
 installed mysql-connector-python package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 mysql-connector-python
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Its seems does not want to force uninstall :-( too

---

### Post by mas192 on 2019-06-21
Also this what I get for your previous question
```
sudo systemctl status mysql
#result
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: en
   Active: active (running) since Fri 2019-06-21 09:37:19 PDT; 1h 1min ago
     Docs: man:mysqld(8)
           http://dev.mysql.com/doc/refman/en/using-systemd.html
  Process: 1145 ExecStartPre=/usr/share/mysql-8.0/mysql-systemd-start pre (code=
 Main PID: 1221 (mysqld)
   Status: "SERVER_OPERATING"
    Tasks: 39 (limit: 4915)
   CGroup: /system.slice/mysql.service
           &#9492;&#9472;1221 /usr/sbin/mysqld


Jun 21 09:37:18 mirraclemsi systemd[1]: Starting MySQL Community Server...
Jun 21 09:37:19 mirraclemsi systemd[1]: Started MySQL Community Server.



```

---

### Post by Bashing-om on 2019-06-21
mas192: Well ! Not -

Let's step up a notch and see if:
```

sudp apt autoremove -- purge mysql-connector-python

```
will prove to be effective.

Mind ya it is possible that the new install will overwrite what is current, but, I just do not know for certain.
However, what we definitely have to address is that  "1 to remove and 30 not upgraded." which means we have to resolve mysql-connector-python before we can complete the upgrades.
I am very reluctant to "force" the removal :( As that can leave a real mess to clean up.

[INDENT][INDENT]gotta be a way forward
[/INDENT][/INDENT]

---

### Post by deadflowr on 2019-06-21
I think mysql-connector-python is only [the source package]("https://packages.ubuntu.com/source/bionic/mysql-connector-python") and the actual package should be python-mysql.connector.
Or python2-mysql.connector.

---

### Post by Bashing-om on 2019-06-21
Oh Yes !
deadflowr is onto something there !

mas192
what results:
```

sudo apt autoremove --purge python-mysql.connector

```

-forward progress ?-

---

### Post by mas192 on 2019-06-21
Ah it make me want to cry now, Bashing-om

```
sudo apt autoremove --purge mysql-connector-python
#output
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-connector-python
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,362 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 191601 files and directories currently installed.)
Removing mysql-connector-python (8.0.16-1ubuntu18.04) ...
/var/lib/dpkg/info/mysql-connector-python.postrm: 1: /var/lib/dpkg/info/mysql-connector-python.postrm: pyversions: not found
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'distutils.sysconfig'
dpkg: error processing package mysql-connector-python (--remove):
 installed mysql-connector-python package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 mysql-connector-python
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

```
sudo apt autoremove --purge python-mysql.connector#output
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'python-mysql.connector' is not installed, so not removed
The following packages will be REMOVED:
  libpython-stdlib* mysql-connector-python python* python-minimal*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,187 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 191684 files and directories currently installed.)
Removing mysql-connector-python (8.0.16-1ubuntu18.04) ...
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ModuleNotFoundError: No module named 'distutils.sysconfig'
dpkg: error processing package mysql-connector-python (--remove):
 installed mysql-connector-python package post-removal script subprocess returned error exit status 1
Removing python (2.7.15~rc1-1) ...
Removing libpython-stdlib:amd64 (2.7.15~rc1-1) ...
Removing python-minimal (2.7.15~rc1-1) ...
Errors were encountered while processing:
 mysql-connector-python
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

It seems what ever we do this stays :-(

---

### Post by Bashing-om on 2019-06-21
mas192; Ouch !!

Who wudda thunk it ! I sure did not !

Put them back:
```

sudo apt install --reinstall python2.7 libpython-stdlib python-minimal

```
give me a bit to re-think this sloppyation.

[INDENT]still. gotta be a way
[/INDENT]

---

### Post by mas192 on 2019-06-22
Bashing-om sure will do, I hope this is resolvable without a reinstall. Thanks so much for all you input. I hope we can resolve it.

Wish you a great weekend!!!

---

### Post by mas192 on 2019-06-23
Bashing-om and dead flowr,

I have solved my woes,

here is what I did

```
samjoshva@mirraclemsi:~$ ls -l /var/lib/dpkg/info | grep -i mysql-connector-python
-rw-r--r-- 1 root root       0 Jun 23 00:37 mysql-connector-python.list
-rw-r--r-- 1 root root    7183 Mar 28 11:58 mysql-connector-python.md5sums
-rwxr-xr-x 1 root root     950 Mar 28 11:58 mysql-connector-python.postinst
-rwxr-xr-x 1 root root    1209 Mar 28 11:58 mysql-connector-python.postrm
-rwxr-xr-x 1 root root     283 Mar 28 11:58 mysql-connector-python.prerm
(base) samjoshva@mirraclemsi:~$ sudo rm -r /var/lib/dpkg/info/mysql-connector-python.list
(base) samjoshva@mirraclemsi:~$ sudo rm -r /var/lib/dpkg/info/mysql-connector-python.md5sums 
(base) samjoshva@mirraclemsi:~$ sudo rm -r /var/lib/dpkg/info/mysql-connector-python.postinst 
(base) samjoshva@mirraclemsi:~$ sudo rm -r /var/lib/dpkg/info/mysql-connector-python.postrm 
(base) samjoshva@mirraclemsi:~$ sudo rm -r /var/lib/dpkg/info/mysql-connector-python.prerm 
(base) samjoshva@mirraclemsi:~$ clear



```

After clearing these files apt is working now. Thanks so much for the help :-)

---

### Post by mas192 on 2019-06-23
But I have a new problem, my man commands dont work unless sudo man :-( Any advice to fix it would be awesome. Thanks

---

### Post by oldos2er on 2019-06-23
Please start a new thread for your latest question; and if your original question is answered please mark this thread 'Solved' under Thread Tools at the top of the page.

---

### Post by mas192 on 2019-06-23
oldos2er, thanks will do :-)

---

