---
title: "Package operation failed"
date: 2016-03-04
forum: New to Ubuntu
---

### Post by jw0076 on 2016-03-04
No matter how much I try random forums information, it doesn't work
here is my error

A little background is I just got ubuntu 14.04~ just a few hours ago. I'm trying to access the Ubuntu software center and install programs. This is what I keep recieving

```
InstallArchives() failed: Selecting previously unselected package fraqtive.
(Reading database ...
(Reading database ... 5%
(Reading database ... 10%b
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
(Reading database ... 218756 files and directories currently installed.)
Preparing to unpack .../fraqtive_0.4.6-3_amd64.deb ...
Unpacking fraqtive (0.4.6-3) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up octave (3.8.1-1ubuntu1) ...
error: couldn't read directory /usr/local/share/octave/packages: No such file or directory
error: called from
    rebuild at line 29 column 7
    pkg at line 505 column 25
dpkg: error processing package octave (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qtoctave:
 qtoctave depends on octave; however:
  Package octave is not configured yet.
 dpkg: error processing package qtoctave (--configure):
 dependency problems - leaving unconfigured
Setting up fraqtive (0.4.6-3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Error in function:
Setting up octave (3.8.1-1ubuntu1) ...
error: couldn't read directory /usr/local/share/octave/packages: No such file or directory
error: called from
    rebuild at line 29 column 7
    pkg at line 505 column 25
dpkg: error processing package octave (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qtoctave:
 qtoctave depends on octave; however:
  Package octave is not configured yet.
 dpkg: error processing package qtoctave (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
```

---

### Post by Bashing-om on 2016-03-04
jw0076; Hello;

No good clue yet to what is going on,

The reported error:
> 
(I)nstallArchives() failed: Selecting previously unselected package fraqtive.
Setting up octave (3.8.1-1ubuntu1) ...
error: couldn't read directory /usr/local/share/octave/packages: No such file or directory

What results when we try and re-install 'octave' ?
```

sudo apt-get install --reinstall octave

```

Then depending on what results go back to working the fraqtive issue.

[INDENT][INDENT]a firm foundation
[INDENT][INDENT][INDENT]and push
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

