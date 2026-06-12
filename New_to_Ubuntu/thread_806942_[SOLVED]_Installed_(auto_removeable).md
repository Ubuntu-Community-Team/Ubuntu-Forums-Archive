---
title: "[SOLVED] Installed (auto removeable)"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Bruce M. on 2008-05-25
Hi Folks,

In Synaptic Package Manager's "Status Section" I see a list of files under:

**Installed (auto removable)**

Just what happens to these files?

Will they be "automatically" removed?


Thanks, have a nice day.
Bruce

---

### Post by Inxsible on 2008-05-25
Only if you do one of two things

1) run this command in terminal```
sudo apt-get autoremove
```2) In synaptic itself mark them all for completely remove

---

### Post by Bruce M. on 2008-05-25
> **Inxsible said:**
> Only if you do one of two things

1) run this command in terminal```
sudo apt-get autoremove
```2) In synaptic itself mark them all for completely remove

Hi Inxsible

Does this mean they are "orphans"?

Thanks for responding.
Bruce

---

### Post by Inxsible on 2008-05-25
> **Bruce M. said:**
> Hi Inxsible

Does this mean they are "orphans"?

Thanks for responding.
Bruceno, they are simply not being used by any of the installed apps. there is a slight difference between orphans and unused packages. 

I have seen that some of the gstreamer packages are listed as orphaned on my system, but when I remove them, some of my audio and video files stop working.

BTW, using aptitude over apt-get might save you from having to do autoremove. aptitude remembers the dependencies and automatically removes them if not needed. But I also remember reading that apt-get was also going to do the same since somewhere between Feisty and Gutsy. But I am not sure if thats done yet.

---

### Post by Bruce M. on 2008-05-25
> **Inxsible said:**
> no, they are simply not being used by any of the installed apps. there is a slight difference between orphans and unused packages. 

I have seen that some of the gstreamer packages are listed as orphaned on my system, but when I remove them, some of my audio and video files stop working.

BTW, using aptitude over apt-get might save you from having to do autoremove. aptitude remembers the dependencies and automatically removes them if not needed. But I also remember reading that apt-get was also going to do the same since somewhere between Feisty and Gutsy. But I am not sure if thats done yet.

OK, still learning here.
What does Synaptic Package Manager use to get files:

"apt-get" or "aptitude"?

If apt-get, I'll use it to check for proper file names and use the CLI with "aptitude" to get them.  :)
```
bruloo@bruloo:~$ sudo apt-get autoremove
[sudo] password for bruloo: 
Sorry, try again.
[sudo] password for bruloo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libntfs10 libgtk1.2 tcl8.3 libgtk1.2-common tk8.3
The following packages will be REMOVED:
  libglib1.2ldbl libgtk1.2 libgtk1.2-common libntfs10 tcl8.3 tk8.3
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 8450kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 98548 files and directories currently installed.)
Removing libgtk1.2 ...
Removing libglib1.2ldbl ...
Removing libgtk1.2-common ...
Removing libntfs10 ...
Removing tk8.3 ...
Removing tcl8.3 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
bruloo@bruloo:~$ 

```
Have a good one.
Bruce

---

