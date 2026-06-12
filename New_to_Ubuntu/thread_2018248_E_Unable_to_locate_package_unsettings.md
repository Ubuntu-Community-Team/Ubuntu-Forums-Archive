---
title: "E: Unable to locate package unsettings"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by ResistanZ on 2012-07-06
I've installed Unsettings a bunch of times on this same version of Ubuntu before. But for whatever reason, it's not letting me install it now. I'm using the same codes as I had been before:

```
sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install unsettings
```

and the repository adds correctly, but it can't find the package. Any help would be greatly appreciated.

---

### Post by MG&amp;TL on 2012-07-06
What version of ubuntu are you using? Diesch only seems to build for Oneiric and Precise now. [https://launchpad.net/~diesch/+archive/testing/+packages]("https://launchpad.net/%7Ediesch/+archive/testing/+packages")

---

### Post by ResistanZ on 2012-07-06
I'm using Precise.

Edit: When I use that link you provided and download the .deb and install it, it crashes when I try to run it. I was literally using Unsettings on the same 12.04 I have now a few days ago. I had to reinstall 12.04 yesterday and now all of a sudden it's giving me these problems.

---

### Post by MG&amp;TL on 2012-07-06
> **ResistanZ said:**
> I'm using Precise.

Edit: When I use that link you provided and download the .deb and install it, it crashes when I try to run it. I was literally using Unsettings on the same 12.04 I have now a few days ago. I had to reinstall 12.04 yesterday and now all of a sudden it's giving me these problems.

What's the crash output?

I'm not familiar with the app, but what happens if you run:

```
unsettings
```

from a terminal. Odd that you can't install it though.

---

### Post by ResistanZ on 2012-07-06
```
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject

(unsettings:11518): GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.desktop' does not contain a key named 'computer-icon-visible'
Trace/breakpoint trap (core dumped)
```

Edit: Apparently I somehow upgraded to 12.10 without being aware... Even though it still says I am using 12.04 when I click details. I tried to run MyUnity, which is similar to Unsettings and it says 12.10 isn't supported. Uh, how do I downgrade back to 12.04? :\

---

### Post by MG&amp;TL on 2012-07-06
> **ResistanZ said:**
> ```
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject

(unsettings:11518): GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.desktop' does not contain a key named 'computer-icon-visible'
Trace/breakpoint trap (core dumped)
```Edit: Apparently I somehow upgraded to 12.10 without being aware... Even though it still says I am using 12.04 when I click details. I tried to run MyUnity, which is similar to Unsettings and it says 12.10 isn't supported. Uh, how do I downgrade back to 12.04? :\

Not really possible...how did you do that, anyway?
Can you post output of

```
cat /etc/apt/sources.list
```

---

### Post by ResistanZ on 2012-07-06
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu/ quantal main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ quantal main universe restricted multiverse #Added by software-properties

```

---

### Post by NikTh on 2012-07-06
> **ResistanZ said:**
> ```

deb http://archive.ubuntu.com/ubuntu/ quantal main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ quantal main universe restricted multiverse #Added by software-properties

```

Added somehow quantal (12.10) repositories.. Open terminal and write 
```
software-properties-gtk
``` go to other software and remove quantal repositories.. 
Then run 
```
sudo apt-get update ; sudo apt-get dist-upgrade
```
i hope this will solve your , upgrade to 12.10 , problem

---

### Post by ResistanZ on 2012-07-06
Didn't fix. I even restarted my computer. In Details it still says I am running 12.04 but it's acting like I'm running 12.10.

---

### Post by NikTh on 2012-07-06
See the output of 
```
cat lsb-release && uname -r
```

---

### Post by ResistanZ on 2012-07-06
```
resistanz@SKYNET:~$ cat lsb-release && uname -r
cat: lsb-release: No such file or directory

```

---

### Post by NikTh on 2012-07-06
> **ResistanZ said:**
> ```
resistanz@SKYNET:~$ cat lsb-release && uname -r
cat: lsb-release: No such file or directory

```

Sorry my mistake 

the correct command is 

```
cat /etc/lsb-release && uname -r
```

---

### Post by ResistanZ on 2012-07-06
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu quantal (development branch)"
3.5.0-3-generic

---

### Post by NikTh on 2012-07-06
Give the output of ```
cat /etc/apt/sources.list
```

and 
```
ls /etc/apt/sources.list.d/
```

---

