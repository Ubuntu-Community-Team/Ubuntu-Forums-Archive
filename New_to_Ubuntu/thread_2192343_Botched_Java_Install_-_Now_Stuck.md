---
title: "Botched Java Install - Now Stuck"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by jferreir on 2013-12-07
I installed Oracle Java 7, only to realize there's a newer Java 8. So, I tried to remove Java 7 and then install Java 8, but I messed up somewhere along the way. I can't figure out how to fully remove or install either of them, and I'm getting error messages all over the place. Here's the errors when I try to run sudo apt-get purge oracle-java7/8-installer:

```
jason@jason-All-Series:~$ sudo apt-get purge oracle-java7-installer
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  oracle-java7-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 110 kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 197489 files and directories currently installed.)
Removing oracle-java7-installer ...
Purging configuration files for oracle-java7-installer ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing oracle-java7-installer (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@jason-All-Series:~$ sudo apt-get purge oracle-java8-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  oracle-java8-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 113 kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 197469 files and directories currently installed.)
Removing oracle-java8-installer ...
Purging configuration files for oracle-java8-installer ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing oracle-java8-installer (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 oracle-java8-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@jason-All-Series:~$ 

```

Help?

---

### Post by jferreir on 2013-12-07
Never mind, I figured it out (dumb luck). I tried restarting the computer (figured that would end all processes), but that didn't work. I had to delete the lock from from the lib and cache locations, but I also had to restart for the changes to take effect. I was then able to remove both versions, and I'm now reinstalling Java 8.

---

### Post by kulen19 on 2013-12-09
Would be great if you could mark the thread as SOLVED :) [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

