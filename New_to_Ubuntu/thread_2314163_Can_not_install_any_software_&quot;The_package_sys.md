---
title: "Can not install any software &quot;The package system is broken&quot;"
date: 2016-02-18
forum: New to Ubuntu
---

### Post by Excuse_Me on 2016-02-18
I just installed 15.10 Ubuntu and every time I start up software center I get the following message:
"New software can't be installed because there is a problem with the software currently installed. Do you want to repair this problem now?"
If I click the "Repair" button I get the following message every time:
"Package operation failed, the installation or removal of a software package failed." When I click on 'Details' it looks like this:
```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 278933 files and directories currently installed.) 
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb ... 
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) ... 
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb (--unpack): 
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.10.20150723-0ubuntu1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb 
Error in function:  
dpkg: dependency problems prevent configuration of kde-telepathy-minimal: 
 kde-telepathy-minimal depends on kde-config-telepathy-accounts (>= 15.04.0); however: 
  Package kde-config-telepathy-accounts is not installed. 
 
dpkg: error processing package kde-telepathy-minimal (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kde-telepathy: 
 kde-telepathy depends on kde-telepathy-minimal (= 15.04.20ubuntu1); however: 
  Package kde-telepathy-minimal is not configured yet. 
 
dpkg: error processing package kde-telepathy (--configure): 
 dependency problems - leaving unconfigured 


```

After I click away this error message I go on and search for an app I want to install, for example VLC Media Player. No matter which app I try to install I receive the following message on clicking the installation button:
To install [application], these items must be removed:

Metapackage for installing all the kd telepathy components
kde-telepathy

Metapackage for installing the basic kde telepathy components
kde-telepathy-minimal

When I click "Install Anyway" I get the following message:

"The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:
The following packages have unmet dependencies:

kde-telepathy-minimal: Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
                       Depends: telepathy-connection-manager but it is a virtual package
                       Depends: telepathy-mission-control-5 (>= 1:5.12) but 1:5.16.3-1ubuntu4 is installed"

This is very frustrating because I can't install any software at all until I learn how to do it in terminal, so if anyone has any workaround for this problem, for example if I should delete the kde telepathy packages and if so how I can go about doing it would be much appreciated. Please let me know if any further information about my system is needed.

---

### Post by Excuse_Me on 2016-02-18
I found a guide on how to install Skype on terminal and tried but it  didnt work either, this was the messages from the try in terminal:

```
laptop@laptop:~/Downloads$ sudo dpkg -i skype-4-3-0-37-multi-ubu.deb
[sudo] password for laptop: 
Selecting previously unselected package skype:i386.
(Reading database ... 278933 files and directories currently installed.)
Preparing to unpack skype-4-3-0-37-multi-ubu.deb ...
Unpacking skype:i386 (4.3.0.37-1) ...
dpkg: dependency problems prevent configuration of skype:i386:
 skype:i386 depends on libc6 (>= 2.3.6-6~).
 skype:i386 depends on libc6 (>= 2.7).
 skype:i386 depends on libgcc1 (>= 1:4.1.1).
 skype:i386 depends on libqt4-dbus (>= 4:4.5.3).
 skype:i386 depends on libqt4-network (>= 4:4.8.0).
 skype:i386 depends on libqt4-xml (>= 4:4.5.3).
 skype:i386 depends on libqtcore4 (>= 4:4.7.0~beta1).
 skype:i386 depends on libqtgui4 (>= 4:4.8.0).
 skype:i386 depends on libqtwebkit4 (>= 2.2~2011week36).
 skype:i386 depends on libstdc++6 (>= 4.2.1).
 skype:i386 depends on libx11-6.
 skype:i386 depends on libxext6.
 skype:i386 depends on libxss1.
 skype:i386 depends on libxv1.
 skype:i386 depends on libssl1.0.0.
 skype:i386 depends on libpulse0.
 skype:i386 depends on libasound2-plugins.

dpkg: error processing package skype:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for dbus (1.10.0-1ubuntu1) ...
Errors were encountered while processing:
 skype:i386
laptop@laptop:~/Downloads$ 
```

What should I do so I can install software in Ubuntu?

---

### Post by pauljw on 2016-02-18
"To install [application], these items must be removed:

Metapackage for installing all the kd telepathy components
kde-telepathy

Metapackage for installing the basic kde telepathy components
kde-telepathy-minimal"

Why not try doing what Software Center is telling you to do?  Remove those two metapackages.  

""The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"

Do this, too.  

And stop installing software from outside the repos.  That's a sure fire way to break your system.

---

### Post by goofprog on 2016-02-18
you can use the force switch on the APT-GET tool.  this will help you clear the problem with installing apps okay

---

### Post by Excuse_Me on 2016-02-19
> **pauljw said:**
> "To install [application], these items must be removed:

Metapackage for installing all the kd telepathy components
kde-telepathy

Metapackage for installing the basic kde telepathy components
kde-telepathy-minimal"

Why not try doing what Software Center is telling you to do?  Remove those two metapackages.  

""The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"

Do this, too.  

And stop installing software from outside the repos.  That's a sure fire way to break your system.

When I wrote and asked I obviously didn't know how to uninstall them or what they were or if they were important files or something, that's why I asked! I did however later found out how to locate and delete them:
```

laptop@laptop:~$ sudo apt-get remove kde-telepathy
[sudo] password for laptop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
laptop@laptop:~$ sudo apt-get remove kde-telepathy-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy : Depends: kde-telepathy-minimal (= 15.04.20ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
laptop@laptop:~$ 
```

And I also ran apt-get install -f and 'apt-get -f install' but to no avail. I ended up reinstalling Ubuntu altogether and not I do not have the problem anymore.

If I were to pinpoint the point were my troubles with this started it was when I downloaded an application called "Camera" (camera-app). First of all it didn't work and it crashed and after this the problems started showing up. In my configuration at least this app seem to be harmful. I later found an other camera app called Kamerka which I am now running..

---

### Post by buzzingrobot on 2016-02-19
Software you install after you've found it on some random web site will sometimes install a new repository on your system.  When you run an update or try to install a package, *all* the repositories on your system are checked.  The package manager will attempt to use packages in a third-party unofficial repository to resolve dependencies (it assumes we know what we are doing when we put them there). That often creates situations where a dependency *cannot* be resolved.

Launch the "Software & Updates" tool and click the "Other Software" tab to see what, if any, other repo have been added. If you find some, disable them and try again. 

Bottom line:  This is not Windows. Software does not install itself into autonomous little directories that include every other piece of dependent code.  (Among other things, that's a security risk.)

---

### Post by pauljw on 2016-02-19
Hey Excuse_Me, I apologize if I came across a bit harsh, I didn't intend to.  I'm happy to hear that you were able to get your computer back up and running.  

Going by what you wrote, I got the impression that you were searching for software on the web and downloading it to install.  I hope you understand that that is a very insecure way to acquire software.  Our repositories have over 40,000 packages available to us that have been tested and are known to work without breaking our OS.(most of the time)  I believe that's why you saw all those missing dependencies when you attempted to install skype, the package manager would have known about them and brought them along automagically.  It's really quite impressive when you think about it.

Anyway, welcome to Ubuntu.  I recommend taking time to learn about linux and how it works, do your best to forget about Windows. If you can't, at least try not to compare the two because they have nothing much in common in practice or philosophy.  And most importantly, enjoy your new found freedom.  :)

---

### Post by hgebel on 2016-03-08
> **pauljw said:**
> "To install [application], these items must be removed:

Metapackage for installing all the kd telepathy components
kde-telepathy

Metapackage for installing the basic kde telepathy components
kde-telepathy-minimal"

Why not try doing what Software Center is telling you to do?  Remove those two metapackages.  

""The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"

Do this, too.  

And stop installing software from outside the repos.  That's a sure fire way to break your system.

This isn't caused by installing software from outside the repos. It's a known critical bug ([https://bugs.launchpad.net/kubuntu-ppa/+bug/1451728](https://bugs.launchpad.net/kubuntu-ppa/+bug/1451728)) in the official repositories caused by attempting to install kubuntu-desktop on a system that already has GNOME or MATE installed. And once you attempt to install kubuntu-desktop on such a system, the system will not let you install or remove anything (without googling for a workaround or asking, which is what the OP was trying to do), so you can't do what Software Center tells you to do.

-Harry

---

### Post by pauljw on 2016-03-09
Thanks for that, good to know.  A few years back I was running PCLinuxOS and was under the impression that desktops could easily be installed and used on a currently installed system, several in fact.  Seems that may no longer be the case, at least with Ubuntu?  

Best to install a system with the desktop environment that you want, ie Kubuntu to have KDE.  Again, thank you.

Paul

---

