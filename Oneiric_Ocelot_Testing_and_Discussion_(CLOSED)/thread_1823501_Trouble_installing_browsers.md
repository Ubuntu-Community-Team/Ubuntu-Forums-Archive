---
title: "Trouble installing browsers"
date: 2011-08-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 1/0 on 2011-08-12
I've tried installing several browsers (Firefox, Chromium, Links2, Midori). They do install yet I get errors:

```
$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-globalmenu
Suggested packages:
  firefox-gnome-support firefox-kde-support latex-xft-fonts
The following NEW packages will be installed:
  firefox firefox-globalmenu
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.6 MB of archives.
After this operation, 37.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric/main firefox i386 6.0~b5+build1+nobinonly-0ubuntu3 [17.6 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ oneiric/main firefox-globalmenu i386 6.0~b5+build1+nobinonly-0ubuntu3 [54.7 kB]
Fetched 17.6 MB in 11s (1,556 kB/s)                                            
Selecting previously deselected package firefox.
(Reading database ... 147917 files and directories currently installed.)
Unpacking firefox (from .../firefox_6.0~b5+build1+nobinonly-0ubuntu3_i386.deb) ...
Selecting previously deselected package firefox-globalmenu.
Unpacking firefox-globalmenu (from .../firefox-globalmenu_6.0~b5+build1+nobinonly-0ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Setting up firefox (6.0~b5+build1+nobinonly-0ubuntu3) ...
update-alternatives: using /usr/bin/firefox to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
update-alternatives: error: alternative link /usr/bin/x-www-browser is already managed by iceweasel-flashplugin.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 6.0~b5+build1+nobinonly-0ubuntu3); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 firefox
 firefox-globalmenu
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This keeps repeating when I update as some of the packages are not installed properly.

```
$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firefox (6.0~b5+build1+nobinonly-0ubuntu3) ...
update-alternatives: error: alternative link /usr/bin/x-www-browser is already managed by iceweasel-flashplugin.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 6.0~b5+build1+nobinonly-0ubuntu3); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 firefox
 firefox-globalmenu
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I just updated from 11.04 to 11.10, so I'm not sure if it's a result of the update or not. Anyone else seen this?

---

### Post by dino99 on 2011-08-12
maybe look at some ppa conflicts (natty/oneiric), have you upgraded them too ?

---

### Post by 1/0 on 2011-08-12
> **dino99 said:**
> maybe look at some ppa conflicts (natty/oneiric), have you upgraded them too ?

Well, I'm note sure. These are my all my sources (none in /etc/apt/sources.list.d/):

```

deb http://archive.ubuntu.com/ubuntu oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb-src http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb http://archive.canonical.com/ubuntu oneiric partner
deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-security multiverse

```

---

### Post by dino99 on 2011-08-12
seems to be clean and you dont have ppa around. If you dont compile yourself then the deb-scr lines can be commented (# above the line)

then you can clean the cache: clean, autoclean, autoremove
and update again

---

### Post by 1/0 on 2011-08-12
Uncommented the *deb-scr* lines, cleaned the cache, updated and reinstalled but the problems sadly remain the same.

---

### Post by SevenMachines on 2011-08-12
For some reason your alternatives for the flash plugin have become very confused. Try uninstalling
$ sudo apt-get purge flashplugin-installer

---

### Post by 1/0 on 2011-08-12
> **SevenMachines said:**
> For some reason your alternatives for the flash plugin have become very confused. Try uninstalling
$ sudo apt-get purge flashplugin-installer

That seems probable. Only problem is:

```

$ sudo apt-get purge flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 188 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 147918 files and directories currently installed.)
Removing flashplugin-installer ...
update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt: invalid status
dpkg: error processing flashplugin-installer (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by SevenMachines on 2011-08-12
What does /var/lib/dpkg/alternatives/iceape-flashpluginlook like?
Should be
```
$ cat /var/lib/dpkg/alternatives/iceape-flashplugin
auto
/usr/lib/iceape/plugins/flashplugin-alternative.so

/usr/lib/flashplugin-installer/libflashplayer.so
50

```Note that you may be able to do something like
```
$ sudo update-alternatives --remove x-www-browser /etc/alternatives/iceape-flashplugin 
# You might need to do this for others such as iceweasel-flashplugin, etc
$ sudo apt-get purge flashplugin-installer
$ sudo apt-get install firefox
```

---

### Post by 1/0 on 2011-08-12
All it has is:

```

$ cat /var/lib/dpkg/alternatives/iceape-flashplugin 
pysupport -

```

---

### Post by SevenMachines on 2011-08-12
Somethings obviously gone horribly wrong when installing flash at some point. Try replacing the contents of 
/var/lib/dpkg/alternatives/iceape-flashplugin  with the correct version I posted earlier and see if that lets you remove flashplugin-installer

---

### Post by 1/0 on 2011-08-12
I've tried to remove it but no go:

```

$ sudo apt-get remove flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-installer
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
3 not fully installed or removed.
After this operation, 188 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148021 files and directories currently installed.)
Removing flashplugin-installer ...
update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt: unexpected end of file while trying to read master file
dpkg: error processing flashplugin-installer (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by dino99 on 2011-08-12
force dpkg to do what you need:

[http://www.debianhelp.co.uk/debianproblem.htm](http://www.debianhelp.co.uk/debianproblem.htm)

---

### Post by cpatrick08 on 2011-08-12
> **dino99 said:**
> seems to be clean and you dont have ppa around. If you dont compile yourself then the deb-scr lines can be commented (# above the line)

then you can clean the cache: clean, autoclean, autoremove
and update again
clean unless the ppa is in the /etc/apt/sources.list.d folder then it would not show up in /etc/apt/sources.list file

---

### Post by 1/0 on 2011-08-12
> **dino99 said:**
> force dpkg to do what you need:

[http://www.debianhelp.co.uk/debianproblem.htm](http://www.debianhelp.co.uk/debianproblem.htm)

I tried this:

```

$ sudo dpkg --force-depends --purge flashplugin-installer
(Reading database ... 148021 files and directories currently installed.)
Removing flashplugin-installer ...
update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt: unexpected end of file while trying to read master file
dpkg: error processing flashplugin-installer (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer

```

Not sure what else to do...

---

### Post by 1/0 on 2011-08-12
> **cpatrick08 said:**
> clean unless the ppa is in the /etc/apt/sources.list.d folder then it would not show up in /etc/apt/sources.list file

The */etc/apt/sources.list.d* folder is empty. All there is, is the sources.list I posted previously. Clean didn't solve anything, sadly.

---

### Post by cariboo on 2011-08-12
IF you pay attention to what the log file is saying you should be able to solve your problem. I noticed this:

> update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt

it looks like you need to remove the iceape-flashplugin, in order to install any browsers.

---

### Post by 1/0 on 2011-08-12
> **cariboo907 said:**
> IF you pay attention to what the log file is saying you should be able to solve your problem. I noticed this:



it looks like you need to remove the iceape-flashplugin, in order to install any browsers.

Yeah. I also noticed that but:

```

$ sudo apt-get purge iceape-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package iceape-flashplugin

```

Is it a part of another package? I mean it's present on my system:

```

$ ls -l /var/lib/dpkg/alternatives/*flash*
-rw-r--r-- 1 root root 111 2011-07-05 20:58 /var/lib/dpkg/alternatives/firefox-flashplugin
-rw-r--r-- 1 root root 109 2011-08-12 17:02 /var/lib/dpkg/alternatives/iceape-flashplugin
-rw-r--r-- 1 root root 113 2011-07-05 20:58 /var/lib/dpkg/alternatives/iceweasel-flashplugin
-rw-r--r-- 1 root root 114 2011-07-05 20:58 /var/lib/dpkg/alternatives/midbrowser-flashplugin
-rw-r--r-- 1 root root 111 2011-07-05 20:58 /var/lib/dpkg/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root 120 2011-07-05 20:58 /var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
-rw-r--r-- 1 root root 113 2011-07-05 20:58 /var/lib/dpkg/alternatives/xulrunner-flashplugin

```

---

### Post by SevenMachines on 2011-08-12
> **1/0 said:**
> I've tried to remove it but no go:

```

update-alternatives: error: /var/lib/dpkg/alternatives/iceape-flashplugin corrupt: unexpected end of file while trying to read master file

```
Add an empty line to the bottom of the file, any improvement?

---

### Post by 1/0 on 2011-08-13
> **SevenMachines said:**
> Add an empty line to the bottom of the file, any improvement?

No, sadly no change with extra lines. I left it as above (i.e. not as borked as before).

---

### Post by 1/0 on 2011-08-14
I finally solved it. I decided to start removing the package manually. But when inspecting the files, I realized all the *flash* files in the folder was corrupt (with loads of ?binary? file symbols s.a. @^@^@^). All I did was to rename all the *flash* files in order for dpkg to work. 

I really don't know what screwed this up but something went dead wrong. I hope this might help others.

Thanks so much for your help guys. I really appreciate it!

---

