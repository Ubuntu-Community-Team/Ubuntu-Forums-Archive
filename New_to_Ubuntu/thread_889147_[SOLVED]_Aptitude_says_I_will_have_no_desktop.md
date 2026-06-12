---
title: "[SOLVED] Aptitude says I will have no desktop?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-08-13
Upon sudo-ing the following: 

mark@Lexington-19:~$ sudo aptitude install gimp 
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  gimp gimp-python libgimp2.0 
The following packages have been kept back:
  transmission-common transmission-gtk 
The following packages will be upgraded:
  gimp-data 
3 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 14.6MB of archives. After unpacking 1847kB will be used.
The following packages have unmet dependencies:
  gimp: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is installed.
  libgimp2.0: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is installed.
  gimp-python: Depends: gimp (= 2.4.5-1ubuntu2) but 2.4.6-1ubuntu1~hardy1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
gimp
gimp-python
**ubuntu-desktop**

Keep the following packages at their current version:
gimp-data [2.4.5-1ubuntu2 (hardy, now)]
libgimp2.0 [2.4.5-1ubuntu2 (hardy, now)]

Leave the following dependencies unresolved:
gimp-data recommends gimp
Score is -9803

Accept this solution? [Y/n/q/?] Y
The following packages will be automatically REMOVED:
  gimp gimp-python ubuntu-desktop 
The following packages have been kept back:
  gimp-data libgimp2.0 transmission-common transmission-gtk 
The following packages will be REMOVED:
  gimp gimp-python ubuntu-desktop 
0 packages upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 12.4MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 147133 files and directories currently installed.)
Removing ubuntu-desktop ...


Now I'm afraid to reboot (EVER!). Can anybody tell me whether I will have a desktop or no. And if NO, how do I get one back short of a clean install?

---

### Post by halitech on 2008-08-13
in the terminal, just enter
```
sudo apt-get install ubuntu-desktop
``` and it will reinstall the desktop

---

### Post by zebulon M on 2008-08-13
Check if gimp isn't already installed... 

Otherwise, that message isn't really a problem, you will not uninstall your desktop. It is still kinda strange.

---

### Post by snowpine on 2008-08-13
It is nothing to worry about. :) Ubuntu-desktop is a "meta" package, which means it's just a list of other packages to install. Removing it doesn't actually remove anything important... just the list.

Now, it is curious that you got this message in the first place. Basically what it is telling you is that gimp was already installed (it is one of the packages listed in ubuntu-desktop) and you are trying to install a different version of it?

---

### Post by ddixonr on 2008-08-13
Go ahead and reboot when it is convenient, and use the above code to install gnome if, by some chance, it isn't installed.

---

### Post by Mark_in_Hollywood on 2008-08-13
Upon reboot, "things" seem fine.

When I made the dist-upgrade back April, at that time the entire upgrade never finished. I kept getting offered partial upgrades. After a while that stopped . . . well, I guess I don't completely remember. The 'puter has been good.

But today, I saw the line in aptitude with the -f argument, so I ran it to see if I had dependency problems. What I saw was that Transmission's and Gimp's dependencies seem to be in conflict. Weird. Anyway. I think things are, good here. As I said, I re-booted.

---

