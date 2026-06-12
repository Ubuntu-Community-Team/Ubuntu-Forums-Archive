---
title: "Can't install updates or programs Ubuntu 12.04LTS"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by Yin1520 on 2012-06-25
Hello everyone, 
I am having some issues after upgrading from 11.04 to 12.04. Whenever I try to install the recommended updates in the update manager center it says that the installation failed and I get the following error message:

```
(Reading database ... 85%%
(Reading database ... 90%%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'network-manager-gnome': Input/output error
Error in function: 

```

and that's it. Reading some posts in the forum where they have similar problems, I found they suggest to run an apt-get update and upgrade from a terminal so I did, but I keep getting error messages

```
Get:97 http://archive.ubuntu.com/ubuntu/ precise-updates/main python-ubuntuone-control-panel all 3.0.1-0ubuntu1 [27.2 kB]
Fetched 92.4 MB in 4min 10s (368 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 90%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'network-manager-gnome': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

And I get something very similar whenever I try to install software from the software center. 

Does anyone know what's going on here? Please help :)

---

### Post by jmfal on 2012-06-25
Welcome to Ubuntu,

Part of your problem is that you have to upgrade from 11.04 to11.10 then to12.04

Here is a link,  click on "read release notes" in the first line and read everything

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

---

### Post by Paqman on 2012-06-25
Hmm, looks gnarly. Bit of a stab in the dark, but what output do you get from:
```
sudo dpkg configure -a
sudo apt-get -f install
```
You might also want to have a look in the logs at /var/log/apt/history.log and /var/log/dpkg.log

---

### Post by nipunshakya on 2012-06-25
Hello Yin... its better you install ubuntu 12.04 freshly rather than getting your head burnt with update issues from 11.04 to 12.04 directly... A fresh installation will minimize the errors as less as possible...
Just download a fresh iso from ubuntu's website for ubuntu 12.04 and make a fresh and clean installation rather than upgrade...

Goodluck

---

### Post by Yin1520 on 2012-06-25
@jmfal 
Hi, thanks for your reply. 
Well, I did the upgrades using the update manager center, and I am pretty sure that I did upgrade to the 11.10 to the 12.04 (I did one right after the other so I never actually used the 11.10). Maybe one of them went wrong?

@Paqman

Hi, this is what I get from the first code:

```
sudo dpkg configure -a
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

```

And this is for the second one:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 100 not upgraded.
```

What should I look for in the log files? (I am totally new to ubuntu, sorry)

---

### Post by ajgreeny on 2012-06-25
Should be ```
sudo dpkg --configure -a
``` I think.  The -- was missing.

---

### Post by Paqman on 2012-06-26
> **ajgreeny said:**
> Should be ```
sudo dpkg --configure -a
``` I think.  The -- was missing.

Yes, my mistake, sorry!

---

### Post by jmfal on 2012-06-26
with dpkg command ::
 one space between  dpkg and --conf   and two spaces between " configure  -a

---

### Post by napzilla on 2013-02-07
I'm having the same problem, but only with one particular update, Ubuntu Desktop Guide (ubuntu-docs). Oddly enough, all the other updates seem to install correctly, but this stubborn little update consistently refuses. When I attempt to update it, either through the Update Manager or apt, it returns an Input/Output Error regarding the directory /usr/share/help/az/ubuntu-help[/CODE].

```
sudo dpkg --configure -a
```
runs and exits with no errors.

```
sudo apt-get -f install
```
returns 0 packages upgraded, newly installed, and to remove, and 1 package not upgraded...

I'm a bit puzzled as to what the problem is, and whether it can be fixed. Any help would be much appreciated. :D

---

