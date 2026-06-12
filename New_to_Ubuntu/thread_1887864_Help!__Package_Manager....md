---
title: "Help!  Package Manager..."
date: 2011-11-28
forum: New to Ubuntu
---

### Post by nickyn on 2011-11-28
Okay!  I've been living with this for a while now, and I just tried to install something new onto my computer and I can't.  I thought it was just the updater was messed, but apparently I can't install anything new until I figure out how to fix this.  And I know VERY little about computers.  So, here we go!

When I open the Update Manager, I get this error message:
An unresolved problem occurred while intializing the package information.  Please report this bug against the 'update-manager' package and include the following error message: 'E:Encountered a section with no Package: header, E: Problem with MergeList /var/ib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

When I open Synaptic Package Manager, I get this error message:
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

And, when I try to install something, I get this error message:
This is a major failure of your software management system.  Please check for broken packages with Synaptic Package Manager, check the files permissions and correctness of the file 'etc/apt/sources.list' and reload the software information with 'sudo apt-get update' and 'sudo apt-get install -f'.

If anyone could give me hand, literally step-by-step for dummies, on how to fix this it would be much appreciated.  Thanks in advance!  Oh, and I have 10.4 version...I can't change my info because I haven't posted 50 times or something like that.

---

### Post by ExileAmongYou on 2011-11-28
The first thing to try would be the suggestion it gives you in that last error message: Open up a terminal, and paste in 
```
sudo apt-get install -f
```
then press enter.
After that, try
```
sudo apt-get update
```
You will have to type in your password, but that should be it. Copy the output you get from those commands and post it here if you still have the same problem.

---

### Post by nickyn on 2011-11-28
Awesome, that worked.  Thanks SO much!

---

