---
title: "bashful bash"
date: 2018-02-04
forum: New to Ubuntu
---

### Post by Walter_M_Green_III on 2018-02-04
ls /bin/bash reports no such file or directory. 
apt-get reports  bash not installed. 
Running a bash script reports bash is not installed. 
Package manager(s) (synaptic, et cetera) report it is installed. 
When using a package manager to reinstall bash, the package manager reports: 

E: /var/cache/apt/archives/bash_4.3-7ubuntu1.7_amd64.deb: subprocess new pre-removal script returned error exit status 2

How fix it? I do need bash.

---

### Post by Walter_M_Green_III on 2018-02-04
P.S. using 14.04 and can not upgrade. Last time I tried to upgrade 16.xx installed (seemingly) then on reboot would not run. This has happened on both my laptop and desktop.

---

### Post by wildmanne39 on 2018-02-04
*Thread moved to **New to Ubuntu, a more appropriate forum**.*

---

### Post by Walter_M_Green_III on 2018-02-04
Nothing will install but got bash working by downloading package and extracting bash file that goes into /bin (/bin/bash) and replaced it, but package manager still mon't install anything because of the following:

Get the following error:
E: bash-completion: package bash-completion is not ready for configuration  cannot configure (current status `half-installed')

Changes Applied windows says:
(synaptic:10913): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 428651 files and directories currently installed.)
Preparing to unpack .../bash_4.3-7ubuntu1.7_amd64.deb ...
Unpacking bash (4.3-7ubuntu1.7) over (4.3-7ubuntu1.7) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
install-info: warning: no info dir entry in `/usr/share/info/smbc.info.gz'
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up bash (4.3-7ubuntu1.7) ...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode
dpkg: error processing package bash-completion (--configure):
 package bash-completion is not ready for configuration
 cannot configure (current status `half-installed')
Processing triggers for menu (2.1.46ubuntu1) ...
Errors were encountered while processing:
 bash-completion
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by Impavidus on 2018-02-05
> **Walter_M_Green_III said:**
> 
apt-get reports  bash not installed. 
...
Package manager(s) (synaptic, et cetera) report it is installed. 


As apt-get and synaptic are just different interfaces to the same package manager, something must be really wrong. And bash should be installed by default.

What do you get from```
dpkg -l | grep bash
dpkg -l | egrep -v '^ii|^rc'
```The first should tell us the status of all bash-related packages according to the package manager, the second should list all packages in an unclean state.

Alternatively, we could try and help you get to 16.04. With a system that's broken already, a clean install would be much better than a release upgrade. I suggest you verify that the backups of your important documents are up to date. I expect it would be the fast way out of your problem.

---

### Post by vasa1 on 2018-02-05
> **Impavidus said:**
> ... **And bash should be installed by default**.

... With a system that's broken already, **a clean install would be much better** than a release upgrade. I suggest you verify that the backups of your important documents are up to date. I expect it would be the fast way out of your problem.
+1 to that!

---

### Post by Walter_M_Green_III on 2018-02-05
```

$ dpkg -l | grep bash
ii  bash                                                  4.3-7ubuntu1.7                                      amd64        GNU Bourne Again SHell
iHR bash-completion                                       1:2.1-4ubuntu0.2                                    all          programmable completion for the bash shell
ii  command-not-found                                     0.3ubuntu12                                         all          Suggest installation of packages in interactive bash sessions

```

```

$ dpkg -l | egrep -v '^ii|^rc'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                             Architecture Description
+++-=====================================================-===================================================-============-========================================================================================================================================
iHR bash-completion                                       1:2.1-4ubuntu0.2                                    all          programmable completion for the bash shell

```

I really don't want to loose all the updates, installs and downloads. And yeah bash WAS installed automatically.

I never said I was NEW to Ubuntu, someone moved my post here, my post was about an installation problem with bash, I originally had this post in Installation and Software. Someone was "helpful" and moved it here.

While building a number of bash scripts, I got so used to typing **/bin/bash** that when saving one of the scripts I tried saving the script in the **/bin** directory so I did not need to use the script only in the directory it resides in or only by using **./path/script** and having to know the entire path to the script each usage. So by accident I saved the script to **/bin/bash** after typing **#!/bin/bash** in the head of every script it was a very natural thing to type, and since I had been working on scripts half the night, I did not realize I had done so. so moving **music_check** script to **/bin** became **sudo mv music_check /bin/bash**

How I got here doesn't matter so much as why after putting **bash** into the **/bin **directory am I still having problems? My scripts all run without complaint but all the package managers fail to install or reinstall anything... hold on a minute. I just tried to upgrade packages like browsers and other miscellaneous apps the system said needed upgrading. All went well until it got to the end. Synaptic reports an error occurred:

```

E: bash-completion: package bash-completion is not ready for configuration  cannot configure (current status `half-installed')

```

As you can see from the following it also updated some system files. (I am only showing the end of the updates where the error occurred.

```

Setting up linux-image-generic-lts-xenial (4.4.0.112.96) ...
Setting up linux-headers-4.4.0-112 (4.4.0-112.135~14.04.1) ...
Setting up linux-headers-4.4.0-112-generic (4.4.0-112.135~14.04.1) ...
Setting up linux-headers-generic-lts-xenial (4.4.0.112.96) ...
Setting up linux-generic-lts-xenial (4.4.0.112.96) ...
Setting up palemoon (27.7.2~repack-1) ...
Setting up firefox-mozilla-build (58.0.1-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.14) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Errors were encountered while processing:
 bash-completion
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

So what do you think? I have never encountered this problem before, all from a simple mistake.

---

### Post by Impavidus on 2018-02-05
The proper place to store your own programs is ~/.local/bin/ for your own use or /usr/local/bin/ for system-wide installation. Those directories are by default part of your PATH. Leave /bin/ and /usr/bin/ for the package manager.

When you manually restored the bash executable, I hope you took the correct version for Ubuntu 14.04, right? Because a version mismatch could cause all kinds of problems.

What do you get from```
sudo apt-get update
sudo apt-get --reinstall install bash-completion
```

---

### Post by Walter_M_Green_III on 2018-02-06
I did as suggested above, I had done this before I had copied the **bash** file from the archive and placing it back into the **/bin** directory and it failed, this time however all seemed to go well. A popup came up this time and said to reboot. So I did without problem. I then tried doing something simple by adding the docs for bash and got this:

```

(synaptic:3674): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
Selecting previously unselected package bash-doc.
(Reading database ... 461046 files and directories currently installed.)
Preparing to unpack .../bash-doc_4.3-7ubuntu1.7_all.deb ...
Unpacking bash-doc (4.3-7ubuntu1.7) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
install-info: warning: no info dir entry in `/usr/share/info/smbc.info.gz'
Setting up bash-doc (4.3-7ubuntu1.7) ...

```

This did not throw up a warning screen or cause problems, though as you see this warning was made in the install screen of the package manager. I decided to try something else. I clicked the upgrade button on the package manager, this was to look for upgrades for various installed packages. It showed me packages that needed upgrading so I hit apply. Everything went perfectly. Saw no warnings except for the G_lib error that seems to be going on for years in 14.04 and other versions of ububntu. Only I always ask about ubuntu 14.04 when actually prefer kubuntu 14.04, have been using KDE long before KDE4.

All is well that ends well.

Thanks to everyone for the help.

---

### Post by Impavidus on 2018-02-07
> **Walter_M_Green_III said:**
> 
```

install-info: warning: no info dir entry in `/usr/share/info/smbc.info.gz'

```


Sounds like a small problem in whatever package that supplies smbc.info.gz. It does no harm to your system.

---

