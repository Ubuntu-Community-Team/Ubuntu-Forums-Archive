---
title: "problem in ubuntu software center in 12.04"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by mahajan on 2012-06-08
$ software-center

2012-06-08 12:29:34,652 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2012-06-08 12:29:34,652 - dbus.proxies - ERROR - Introspect error on :1.218:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-06-08 12:29:34,677 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-06-08 12:29:34,682 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-06-08 12:29:34,916 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
Killed
dm@ubuntu:~$ 
dm@ubuntu:~$ software-center
2012-06-08 12:29:57,443 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-06-08 12:29:57,453 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-06-08 12:29:57,677 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file





the software center is not working
whaen i have opened or click it it gives a blank white display nothing else 
even my dash home is  also showing nothing in application section it is showing blank




now where is actually  problem 
please solve it as fast as soon as possible .many software i have to install

---

### Post by MG&amp;TL on 2012-06-08
Best thing you can do is make it better.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+filebug](https://bugs.launchpad.net/ubuntu/+source/software-center/+filebug)

---

### Post by mahajan on 2012-06-08
$ software-center
2012-06-08 12:57:32,012 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2012-06-08 12:57:32,012 - dbus.proxies - ERROR - Introspect error on :1.247:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2012-06-08 12:57:57,066 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-06-08 12:57:57,069 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-06-08 12:57:57,286 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file


stilL Same error

---

### Post by mahajan on 2012-06-08
and nothing is displayed on application section in dash home

---

### Post by cortman on 2012-06-08
First, file a bug report like MG&TL suggested.
Then your best bet is probably to uninstall and reinstall Software Center- this has fixed about every USC problem I've come across.

```
sudo apt-get install --reinstall software-center
```

---

### Post by mahajan on 2012-06-14
> **cortman said:**
> First, file a bug report like MG&TL suggested.
Then your best bet is probably to uninstall and reinstall Software Center- this has fixed about every USC problem I've come across.

```
sudo apt-get install --reinstall software-center
```

sir even i have tried this also but still the problem remain the same
and even nothing is displayed in application section of dash home .earlier it was working well .what should be done now
software-center is showing blank white screen and is not responding

---

### Post by mahajan on 2012-06-15
sir please tell me alternate solution to solve my problem.still my problem is same .should i reinstall ubuntu again for that.

---

### Post by afixane on 2012-06-15
> **mahajan said:**
> sir please tell me alternate solution to solve my problem.still my problem is same .should i reinstall ubuntu again for that.

No. try to Purge it.

---

### Post by firekage on 2012-06-15
> **afixane said:**
> No. try to Purge it.

So he should do, if i'm right:

```
sudo apt-get remove --purge software-center
``` 

(i'm not sure but i saw also something like this: 

```
sudo apt-get remove software-center --purge
``` but i'm not sure which is right). After it there should be:

```
sudo apt-get install software-center
```?

---

### Post by SDX0 on 2012-06-15
"apt-get purge software-center" works too.

---

### Post by cortman on 2012-06-15
> **mahajan said:**
> sir even i have tried this also but still the problem remain the same
and even nothing is displayed in application section of dash home .earlier it was working well .what should be done now
software-center is showing blank white screen and is not responding

Do you get this white screen effect for other programs or processes? If so that could be a graphics driver issue.

---

### Post by mahajan on 2012-06-21
> **SDX0 said:**
> "apt-get purge software-center" works too.

even tried this 

dm@ubuntu:~$ sudo apt-get install software-center
sudo: /var/lib/sudo writable by non-owner (040777), should be mode 0700
[sudo] password for dm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
software-center is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bleachbit : Depends: python-central (>= 0.6.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
  

this is the output

---

### Post by mahajan on 2012-06-21
> **cortman said:**
> Do you get this white screen effect for other programs or processes? If so that could be a graphics driver issue.

sir i have told you only problem in software center is coming and in dash home where it doesn't show any application installed

---

