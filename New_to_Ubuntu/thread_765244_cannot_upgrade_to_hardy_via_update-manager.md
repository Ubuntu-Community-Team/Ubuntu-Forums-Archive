---
title: "cannot upgrade to hardy via update-manager"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by philphil on 2008-04-24
Hi,

I'm trying to upgrade to Hardy from Gutsy using update-manager.  When I load update-manager I can see the link new distribution release '8.04 LTS' is available and when I click the "Upgrade" button next to that Update Manager goes grey after a few seconds and the loading mouse icon appears and nothing happens....can anyone help?  Is there a way to upgrade via the terminal?

Cheers

---

### Post by vishzilla on 2008-04-24
The servers will be busy next few days due to excess of traffic and downloading. You are probably better off downloading the torrent rather than a direct upgrade. You can download the alternate ISO to upgrade via the CD.
The below commands will upgrade you to 8.04 via the update manager
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Seisen on 2008-04-24
> **philphil said:**
> Hi,

I'm trying to upgrade to Hardy from Gutsy using update-manager.  When I load update-manager I can see the link new distribution release '8.04 LTS' is available and when I click the "Upgrade" button next to that Update Manager goes grey after a few seconds and the loading mouse icon appears and nothing happens....can anyone help?  Is there a way to upgrade via the terminal?

Cheers

Try sudo update-manager from the terminal and post what it says.

---

### Post by philphil on 2008-04-24
wow, thanks to both vishzilla and Seisen for your prompt responses

vishzilla: I ran sudo apt-get update and it completed without any errors and when I run sudo apt-get dist-upgrade:
```

phil@phil-laptop:~$ sudo apt-get dist-upgrade
[sudo] password for phil:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phil@phil-laptop:~$ 

```

Strange no?  Does it think I've already updated?


Seisen: running sudo update-manager: 

```

phil@phil-laptop:~$ sudo update-manager

** (update-manager:9338): WARNING **: Irregular conf file line(1):
# this file contains quirks

** (update-manager:9338): WARNING **: Irregular conf file line(1):
# list prgname that need to be ignored below

** (update-manager:9338): WARNING **: Irregular conf file line(1):
#

** (update-manager:9338): WARNING **: Irregular conf file line(0):

warning: could not initiate dbus

```

Update manager then loads successfully....aha! and when I click upgrade it works!!! thanks, must have been a busy server or something earlier I guess?

---

### Post by psychofish25 on 2008-04-24
I believe you need to run those top two commands in order. The update command lists all the available updates, and the dist-upgrade command will upgrade ubuntu, or so I believe.

---

### Post by philphil on 2008-04-24
> **psychofish25 said:**
> I believe you need to run those top two commands in order. The update command lists all the available updates, and the dist-upgrade command will upgrade ubuntu, or so I believe.

yep, I did that...

---

### Post by bullring on 2008-04-24
> **Seisen said:**
> Try sudo update-manager from the terminal and post what it says.

here is what I get: 
```
bullring@lappy:~$ sudo update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 51, in <module>
    import subprocess
ValueError: bad marshal data
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 51, in <module>
    import subprocess
ValueError: bad marshal data

```
any help you could provide would be great.

---

### Post by philphil on 2008-04-24
ok I figure it's not working because of server trouble, I got somewhere earlier but now I'm back to the first problem I described in the original post.  My money's on the servers being overloaded, we should all just relax...

---

### Post by Crafty Kisses on 2008-04-24
> **philphil said:**
> ok I figure it's not working because of server trouble, I got somewhere earlier but now I'm back to the first problem I described in the original post.  My money's on the servers being overloaded, we should all just relax...

Yes, I'm not going to start downloading Ubuntu 8.04 until tomorrow, I'd suggest you wait as well.

---

### Post by afilonov on 2008-04-24
> **vishzilla said:**
> The servers will be busy next few days due to excess of traffic and downloading. You are probably better off downloading the torrent rather than a direct upgrade. You can download the alternate ISO to upgrade via the CD.
The below commands will upgrade you to 8.04 via the update manager
```
sudo apt-get update
sudo apt-get dist-upgrade
```

You also need to change your distribution pointers (GUI update manager does it for you). So, the real sequence:

sudo apt-get update
nano /etc/apt/sources.txt (change all links by replacing gutsy with hardy)
sudo apt-get dist-upgrade

---

### Post by afilonov on 2008-04-24
> **vishzilla said:**
> The servers will be busy next few days due to excess of traffic and downloading. You are probably better off downloading the torrent rather than a direct upgrade. You can download the alternate ISO to upgrade via the CD.
The below commands will upgrade you to 8.04 via the update manager
```
sudo apt-get update
sudo apt-get dist-upgrade
```

You also need to change your distribution pointers (GUI update manager does it for you). So, the real sequence:

sudo apt-get update
nano /etc/apt/sources.list (change all links by replacing gutsy with hardy)
sudo apt-get dist-upgrade

---

