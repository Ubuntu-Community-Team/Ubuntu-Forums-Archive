---
title: "Maverick DPKG error"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by abhinavnain on 2011-09-12
hey well um a newbie to UBUNTU but i know how to install software/packages using LINUX TERMINAL by apt-get but from past few days whenever I try to do so the following error shows up ..
*This was when I tried to install SKYPE*

root@ubuntu:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following NEW packages will be installed:
skype
0 upgraded, 1 newly installed, 0 to remove and 293 not upgraded.
11 not fully installed or removed.
Need to get 23.6MB of archives.
After this operation, 29.9MB of additional disk space will be used.
Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner skype i386 2.2.0.35-0maverick1 [23.6MB]
Fetched 23.6MB in 6min 35s (59.6kB/s) 
Setting up tar (1.23-2ubuntu2) ...
update-alternatives: error: cannot append to /usr/local/var/log/alternatives.log : No such file or directory
dpkg: error processing tar (--configure): subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
tar
E: Sub-process /usr/bin/dpkg returned an error code (1)

the similar things shows up in synaptic and ubuntu software center also..

---

### Post by SeijiSensei on 2011-09-12
> update-alternatives: error: cannot append to /usr/local/var/log/alternatives.log : No such file or directory

As far as I can tell, there is no /usr/local/var directory in Maverick.  I have the same version of Skype installed as you do, and that directory doesn't exist on my system.  alternatives.log is stored with all the other logs in /var/log.

Since you say this happens with other package managers, you must have made some change to the directories apt and dpkg expect to use.  A quick fix might be this:

```
sudo ln -s /var /usr/local
```

This will create a "symbolic link" to the log directory under /usr/local.  The alternatives log will then be available to the installer.  After you make the link, use "ls /usr/local/var/log" to make sure the link works correctly.  You should see all the log files like "syslog" and, probably, "alternatives.log".

That said, this is an unnecessary kludge.  Frankly, if you don't have much invested in this installation, I'd just reinstall Maverick from the CD.

---

### Post by abhinavnain on 2011-09-12
Sorry Sir but that didn't worked for me. Anyways thanks 
And I think that re-installation Is the only option left for me.

Well the new story is that I accidently changed the log dir so what I did that I just copied the alternatives.log from /var to /usr/local/var/log
AND IT WORKED ..!..
Anyways thanks..

---

