---
title: "It's been a day and a half since I've first try to get flash on firefox."
date: 2012-01-13
forum: New to Ubuntu
---

### Post by Water Margins on 2012-01-13
This should have been simple, But it's been such a process, This is the process I was going through in Terminal.

> [SIZE=1]~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 128 not upgraded.
Need to get 0B/22.9kB of archives.
After this operation, 233kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
~$ sudo apt-get install alsa-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  alsa-oss
0 upgraded, 1 newly installed, 0 to remove and 128 not upgraded.
Need to get 32.1kB of archives.
After this operation, 156kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe alsa-oss 1.0.17-3 [32.1kB]
Fetched 32.1kB in 0s (42.5kB/s) 
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)[/SIZE]


How do I fix the error?

---

### Post by RedSingularity on 2012-01-13
Run:

sudo dpkg --clear-avail
sudo apt-get update

---

### Post by drmrgd on 2012-01-13
Rather than installing Flash that way,  you might also try Flash-Aid.  It'll pretty much automate the whole process for you, is very customizable, and fixes a lot of problems that seem to creep up with Flash in Ubuntu.  Check out the mega-thread on it here:

[http://ubuntuforums.org/showthread.php?t=1491268]("http://ubuntuforums.org/showthread.php?t=1491268")

Hope that helps!

---

### Post by Water Margins on 2012-01-13
> **RedSingularity said:**
> Run:

sudo dpkg --clear-avail
sudo apt-get update


Sudo dpkg --clear-avail doesn't visibly do anything for me,  And Sudo Apt-get update brings a list of packages and I have no idea what to do from there.

FLASH-AID gave me the same error I was getting before, only it added two more things and said it was working (it Isn't :()

> [SIZE=1]***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
[sudo] password for *****: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [542kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,998B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [210kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,850B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [244kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [85.4kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,058B]
Fetched 1,160kB in 4s (257kB/s)                              
Reading package lists... Done
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 128 not upgraded.
Need to get 0B/20.8kB of archives.
After this operation, 188kB of additional disk space will be used.
Preconfiguring packages ...
[B]Selecting previously deselected package flashplugin-installer.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `linux-headers-2.6.32-33-generic': Input/output erro[/B]r
E: Sub-process /usr/bin/dpkg returned an error code (2)
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
[/SIZE]I'm starting to think either this computer REALLY shouldn't be running linux, or my Unbuntu is just really outdated. (This was a boot disk I had to use to recover a fatal crash on my laptop that was running WinXP)


*EDIT*

I used another option and flash works! Thanks both of you : )

---

