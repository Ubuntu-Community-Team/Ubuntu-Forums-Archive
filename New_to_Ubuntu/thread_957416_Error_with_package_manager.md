---
title: "Error with package manager"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by mogsmar5 on 2008-10-24
When I run package manager I get this error: ```
An error occurred, Please run Package manager from the right click menu of apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount >0' This usually means the your installed packages have unmet dependencies.
```

This problem arose when I try to install Adobe Reader. When I run 'sudo apt-get install -f' I get this message
```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  acroread
The following NEW packages will be installed
  acroread
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0B/22.8MB of archives.
After this operation, 54.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 162074 files and directories currently installed.)
Unpacking acroread (from .../acroread_7.0.1-0.0.ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_7.0.1-0.0.ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_7.0.1-0.0.ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How can I fix this? I want to sort this out before the release of Intrepid Ibex!

---

### Post by northern lights on 2008-10-24
It appears that you're trying to install a version of adobereader that is not in the repositories from a .deb. You already have the package *adobereader-enu* installed.

*/usr/bin/acroread* is part of *adobereader-enu* and needs to be overwritten to install the .deb

Run```
sudo apt-get autoremove adobereader-enu
```and then try to install again```
sudo apt-get install -f
```

---

### Post by bwang on 2008-10-24
Try ```
sudo apt-get remove acrocread-enu
```

---

### Post by mogsmar5 on 2008-10-24
When I run 'sudo apt-get autoremove adobereader-enu' I get this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  acroread-plugins: Depends: acroread (= 7.0.1-0.0.ubuntu1) but it is not going to be installed
  mozilla-acroread: Depends: acroread (>= 7.0) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

```
If I run 'sudo apt-get install -f' I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  acroread
The following NEW packages will be installed
  acroread
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0B/22.8MB of archives.
After this operation, 54.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 162074 files and directories currently installed.)
Unpacking acroread (from .../acroread_7.0.1-0.0.ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_7.0.1-0.0.ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_7.0.1-0.0.ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

There doesn't seem to be any way round it!

---

### Post by acidsolution on 2008-10-24
Remove the available version of acroread from

/var/cache/apt/archives/

or just run 
```

sudo apt-get clean

and than install acroread


```

---

### Post by mogsmar5 on 2008-11-03
I have; then I just get this:

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  acroread
The following NEW packages will be installed
  acroread
0 upgraded, 1 newly installed, 0 to remove and 41 not upgraded.
2 not fully installed or removed.
Need to get 22.8MB of archives.
After this operation, 54.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse acroread 7.0.1-0.0.ubuntu1 [22.8MB]
```
Fetched 22.8MB in 19min11s (19.8kB/s)                                          
(Reading database ... 162074 files and directories currently installed.)
Unpacking acroread (from .../acroread_7.0.1-0.0.ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_7.0.1-0.0.ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_7.0.1-0.0.ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This just seems to be going in circles. Trying to fix one error is blocked by itself!

---

