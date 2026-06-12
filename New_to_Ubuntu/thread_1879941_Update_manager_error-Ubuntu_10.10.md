---
title: "Update manager error-Ubuntu 10.10:"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by mrob184 on 2011-11-12
I have a fresh install of Ubuntu 10.10 and have been running it for 2 days now and everything was running stable. Last night I played around with some widgets and everything went well. I then installed docky and that went good as well no error messages or problems.
Today I tried installing Stellarium from the Ubuntu software center and all hell broke loose. The istall failed several pkg's were messed up and I tried the steps that were sugested by the OS to fix it.
I cannot get the software center or the update manager to open now and get this message when I try to open the update manager.

'E:Malformed 1st word in Status line, E:Error occured While processing language-support-en (UsePackage2), E:Problem with MergeList /var/lib/dpkg/status, E: The  package lists or status file could not be parsed or opened.'

Any help would be appreciated. 
Thanks.

---

### Post by Horibal on 2011-11-12
I had the same problem and couldn't get around it running from a USB drive.  Eventually I just copied the entire dpkg folder from a working system.  No issues with that so far.  But I wasn't able to update it or remove the bad files unless as root.

My problem is with package headers.  This is the error.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

This happened on another system of mine and I just CDd to the folder and did "rm *.*" to get rid of everything, then "sudo apt-get update" and everything was fine.  Not so much on this system, though.  Advice would be appreciated.

---

### Post by Rubi1200 on 2011-11-13
Hi,
first of all it is extremely dangerous to run an rm command without knowing what it does.

You can completely destroy your whole system!!!

In this situation, the best commands to try first are the following:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second refreshes them.

It is best to copy and paste these commands to avoid syntax or other errors.

---

