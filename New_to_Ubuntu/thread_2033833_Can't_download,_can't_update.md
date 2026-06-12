---
title: "Can't download, can't update"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by sophie2cu2 on 2012-07-27
Hi folks,

Still lost in Ubuntu here.

I'm now having download problems. I wanted to download "Sound Converter", but I'm getting this message:[INDENT]An unhandled error occured
There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
[/INDENT]When I tried to update, I got this:[INDENT]Not all updates can be installed
Run a partial upgrade to install as many updates as possible
[/INDENT]Then:[INDENT]Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
[/INDENT]When I run  "sudo apt-get install -f", I get[INDENT]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
[/INDENT]All of this seems to be related - but who am I to say. This is getting scary. Maybe I should spend more time gardening.

Can anyone help?
Thanks guys,
S

---

### Post by Bufeu on 2012-07-27
Why not run *sudo dpkg --configure -a*?

---

### Post by NikTh on 2012-07-27
Hi, 
please open a terminal and copy paste these commands from here (for accuracy) . One line=One command. Take them with order. 
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
sudo rm -f /var/lib/dpkg/lock 
sudo apt-get update 
sudo dpkg --configure -a 
sudo apt-get dist-upgrade
```Thanks

---

### Post by sophie2cu2 on 2012-08-06
SOLVED

Hi,
Many thanks to all.
It worked.
S

---

