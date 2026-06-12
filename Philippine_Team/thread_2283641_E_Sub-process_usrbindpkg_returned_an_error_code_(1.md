---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-06-23
forum: Philippine Team
---

### Post by janis9 on 2015-06-23
Masters,

When I try to uninstall or install softwares, I always come across this problem, anyone can help?

```

~$ sudo apt-get remove google-chrome-stable
[sudo] password for janis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  google-chrome-stable ttf-mscorefonts-installer
0 to upgrade, 0 to newly install, 2 to remove and 184 not to upgrade.
2 not fully installed or removed.
After this operation, 185 MB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:i386
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 236305 files and directories currently installed.)
Removing google-chrome-stable ...
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up man-db (2.6.1-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)





```

---

### Post by v3.xx on 2015-06-23
Please run
```
sudo apt-get update && sudo apt-get upgrade
```
and post all errors

---

### Post by janis9 on 2015-06-23
I've run the code and the errors are shown below:

```
Unpacking replacement libc-bin ...
Processing triggers for ureadahead ...
Setting up libc-bin (2.15-0ubuntu10.12) ...
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 236202 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.6 (using .../libc6_2.15-0ubuntu10.12_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.12_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by slickymaster on 2015-06-23
> **janis9 said:**
> Masters,

When I try to uninstall or install softwares, I always come across this problem, anyone can help?

```

~$ sudo apt-get remove google-chrome-stable
[sudo] password for janis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  google-chrome-stable ttf-mscorefonts-installer
0 to upgrade, 0 to newly install, 2 to remove and 184 not to upgrade.
2 not fully installed or removed.
After this operation, 185 MB disk space will be freed.
Do you want to continue [Y/n]? y
**[COLOR=#ff0000]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable[/COLOR]**
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:i386
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 236305 files and directories currently installed.)
Removing google-chrome-stable ...
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up man-db (2.6.1-2ubuntu1) ...
**[COLOR=#ff0000]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable[/COLOR]**
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)





```
dpkg management tool is hanged or is still running and did not return lock after its completion. Most often, this is only a transient situation. See [https://wiki.edubuntu.org/DebuggingInstallationIssues#DbDriver_.22config.22_is_locked](https://wiki.edubuntu.org/DebuggingInstallationIssues#DbDriver_.22config.22_is_locked) for more details.

Please open a terminal window to figure out the PID of the process that is holding the lock, by running:```
sudo fuser -v /var/cache/debconf/config.dat
```Take a note of the PID number and then, again in the terminal window```
sudo kill PID_number
sudo kill -9 PID_number  # if the first doesn't work
```Afterwards, run again ```
sudo apt-get update && sudo apt-get upgrade
``` to confirm that everything is working as it should.

---

### Post by matt_symes on 2015-06-23
Hi

You could also trying the time honored Windows trick of rebooting your computer :)

That should also fix it if there is not a stale lock file lying around.

Kind regards

---

### Post by janis9 on 2015-06-23
Thank you so much. Things work well now.:KS

---

### Post by slickymaster on 2015-06-23
You're welcome. Glad you got it solved.

Please mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution for this problem.

---

### Post by mystified123 on 2016-02-21
I found this solution that worked for me !
sudo dpkg -i --force-overwrite /var/cache/apt/archives/cinnamon-translations_2.8.0-20151023040309-trusty_all.deb


Here is the link with all the details!
[http://ubuntuforums.org/showthread.php?t=2304033](http://ubuntuforums.org/showthread.php?t=2304033)

---

