---
title: "Problem with Software Center"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by skeedo on 2012-02-26
Hello! I am brand new to Ubuntu, moving over from FreeBSD and seems incredibly more easy to work with. I love the Software Center, especially compared to the FreeBSD ports tree. 

Problem I'm having is I get 'Package Operation Failed...The installation or removal of a software package has failed' after installing any software. The odd thing is, software still installs fine I just get the error message. I'm led to believe there is an issue somewhere however while installing software/drivers because trying to change to Normal/ Extra visual effects in Appearance attempted to install Nvidia drivers and things went a little haywire. 

I tested out installing Hearts to reproduce the error. Here's what the details button shows:

installArchives() failed: Selecting previously deselected package gnome-games-extra-data. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 183494 files and directories currently installed.) 
Unpacking gnome-games-extra-data (from .../gnome-games-extra-data_2.28.0-0ubuntu1_all.deb) ... 
Selecting previously deselected package gnome-hearts. 
Unpacking gnome-hearts (from .../gnome-hearts_0.3-2ubuntu3_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for python-support ... 
Setting up gnome-games-extra-data (2.28.0-0ubuntu1) ... 
Setting up gnome-hearts (0.3-2ubuntu3) ... 

Hearts installed, works fine and is removable. I just don't know why I'm getting the error message, and I am wondering if the problem could be related to installing hardware drivers as well. Any pointers will be greatly appreciated, thanks!

---

### Post by matt_symes on 2012-02-28
Hi

Welcome to the forums. :D

What's the output of (from a terminal)

```
dpkg -l gnome-games-extra-data
```

Post back results by copying and pasting from the terminal window into your next post. You can also copy and paste from here into the terminal.

Use code tags to make it easier to read; like this

[noparse]```
output from command
```[/noparse]

It will then look like this

```
output from command
```

Kind regards

---

### Post by skeedo on 2012-03-01
```

pit87:~> dpkg -l gnome-games-extra-data
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gnome-games-ex 2.28.0-0ubuntu games for the GNOME desktop (extra artwork)
pit87:~> 

```

---

### Post by matt_symes on 2012-03-01
Hi

Nothing wrong with that output. You are correct. It looks like it did install correctly.

Let's start at the beginning. From the terminal type

```
sudo apt-get update
```

and then

```
sudo apt-get install htop
```

Post back all the text these commands generate.

Kind regards

---

### Post by skeedo on 2012-03-01
Here you are:

```

pit87:~> sudo apt-get update
[sudo] password for skeedo: 
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Reading package lists... Done
pit87:~> 

``````

pit87:~> sudo apt-get install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  firefox-branding
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 63.2kB of archives.
After this operation, 217kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe htop 0.8.3-1ubuntu1 [63.2kB]
Fetched 63.2kB in 0s (127kB/s)
Selecting previously deselected package htop.
(Reading database ... 183655 files and directories currently installed.)
Unpacking htop (from .../htop_0.8.3-1ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up htop (0.8.3-1ubuntu1) ...

Processing triggers for menu ...
E: Directory '/var/log/apt/' missing
E: Directory '/var/log/apt/' missing
pit87:~> 

```MIssing directories the problem?

---

### Post by matt_symes on 2012-03-02
Hi

> E: Directory '/var/log/apt/' missing
E: Directory '/var/log/apt/' missing

> MIssing directories the problem?

Maybe... I have never come accross that error before.

```
sudo mkdir /var/log/apt
```

Has it installed htop correctly ?

```
dpkg -l htop
```

Small L after dpkg.

Post back results after.

Kind regards

---

### Post by skeedo on 2012-03-02
Created the directory with sudo. Here's htop info:

```

pit87:~> dpkg -l htop
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  htop                          0.8.3-1ubuntu1                interactive processes viewer
pit87:~>

```

---

### Post by matt_symes on 2012-03-02
Hi

It installed correctly (the ii in the status line).

After creating the directory /var/log/apt, are you still getting errors when installing software ?

Here's another usefull little package to install and test that.

```
sudo apt-get install sysstat
```

BTW: You will have installed *htop* and *iostat* and you can run them from the terminal by typing their name (but i'm sure you know that anyway).

Also included in the package sysstat are.

> The sysstat package contains the following system performance tools:
  - sar: collects and reports system activity information;
  - iostat: reports CPU utilization and disk I/O statistics;
  - mpstat: reports global and per-processor statistics;
  - pidstat: reports statistics for Linux tasks (processes);
  - sadf: displays data collected by sar in various formats.

Kind regards

---

### Post by skeedo on 2012-03-04
Sysstat is already installed, however I installed Atris with out any error messages. Looks like the missing directory was the problem, thanks!

---

