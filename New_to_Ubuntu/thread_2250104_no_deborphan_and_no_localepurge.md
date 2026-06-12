---
title: "no deborphan and no localepurge"
date: 2014-10-26
forum: New to Ubuntu
---

### Post by WacoJohn on 2014-10-26
```
wacojohbn@wacojohbn-VirtualBox:~$ sudo apt-get install deborphan
[sudo] password for wacojohbn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package deborphan is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'deborphan' has no installation candidate
wacojohbn@wacojohbn-VirtualBox:~$
```

```
wacojohbn@wacojohbn-VirtualBox:~$ sudo apt-get install localepurge
[sudo] password for wacojohbn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package localepurge
wacojohbn@wacojohbn-VirtualBox:~$ 

```

any ideas, ... anyone?

ALSO ... how can I change wacojohbn to wacojohn??

---

### Post by Elfy on 2014-10-26
First two it depends on what version you have installed there.

Both packages are available from Universe

[http://packages.ubuntu.com/search?keywords=localepurge&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=localepurge&suite=default&section=all&arch=any&searchon=names)

[http://packages.ubuntu.com/search?keywords=deborphan&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=deborphan&suite=default&section=all&arch=any&searchon=names)

For the changing name, edit /etc/hostname as root.

---

### Post by vasa1 on 2014-10-26
> **Elfy said:**
> ...
For the changing name, edit /etc/hostname as root.If OP just wants to change it in the terminal prompt then help.ubuntu.com/community/CustomizingBashPrompt may help.

---

### Post by deadflowr on 2014-10-27
Firstly, what is the output for the standard
```
sudo apt-get update
```
and second, which wacojobhn do you want to change?
The system name or the user name, or both.
(The first one is the user, the second, after the @ is the system.)

---

### Post by WacoJohn on 2014-10-27
> **Elfy said:**
> First two it depends on what version you have installed there.

Both packages are available from Universe

[http://packages.ubuntu.com/search?keywords=localepurge&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=localepurge&suite=default&section=all&arch=any&searchon=names)

[http://packages.ubuntu.com/search?keywords=deborphan&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=deborphan&suite=default&section=all&arch=any&searchon=names)

For the changing name, edit /etc/hostname as root.

Thank you very much for the info.  I will try your advice.  Thank you again.

---

### Post by WacoJohn on 2014-10-27
> **deadflowr said:**
> Firstly, what is the output for the standard
```
sudo apt-get update
```
and second, which wacojobhn do you want to change?
The system name or the user name, or both.
(The first one is the user, the second, after the @ is the system.)

Thank you for the sudo apt-get update.  I (obviously) made a typo somewhere ... and would like to correct BOTH from wacojobhn to wacojohn.

---

### Post by deadflowr on 2014-10-27
Firstly, again, did anything odd come out of the update command, like errors or whatnots?
(Since this thread is geared toward fixing that problem, first)
(Or did you solve the initial problem altogether?)

And secondly, the advice of changing the name in /etc/hostname will change the system name, and follow this here
[http://askubuntu.com/questions/34074/how-do-i-change-my-username](http://askubuntu.com/questions/34074/how-do-i-change-my-username)
To learn how to change the username.

Hope it helps.

---

