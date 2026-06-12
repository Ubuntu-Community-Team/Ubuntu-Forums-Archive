---
title: "What to do on first boot?"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by UserJB on 2013-04-27
I'm new to Ubuntu, but have been using Linux for years.  In the Fedora and CentOS world, one of the first things one does after the install is a 'yum update' in order to update the latest packages and patches.  Is there an equivalent in Ubuntu?  If so, what is the exact command?

Also, is there some web page that describes what one typically does after installing Ubuntu (not the installation documents, but the typical things to do afterword, like updating software)?

Thank you.

---

### Post by deadflowr on 2013-04-27
The first thing you should do is get familiar with Ubuntu's layout.

Explore the desktop.

If you press the super key(windows key) and type the word help and hit enter you will get the Ubuntu documentation page. Look it over.

After that, find the software updater and run it, so as to keep your system up to date.

Then either try out the default apps, or open the software center and looksy around  for anything that might pique your interest.

Here's a quick link to the help page

[https://help.ubuntu.com/](https://help.ubuntu.com/)

pick the version you installed.

---

### Post by Frogs Hair on 2013-04-27
If you choose to use the console instead of the update manager see below. There are sites that offer lists of what to do after installing , but these can a matter of preference rather than necessary. 
 
Updates Package List:
```
sudo apt-get update 
```
Installs Packages: ```
sudo apt-get upgrade 
```

Still Valid:[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

Manual: [http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)

---

### Post by TheFu on 2013-04-27
[QUOTE=Frogs Hair;12621727] ```
sudo apt-get upgrade 
```

"upgrade" will install out of date packages only AND will not install newer kernels.
To get the newer kernels, while still staying on the same release, use 
```
sudo apt-get dist-upgrade
```
Don't worry. It will not upgrade from 12.10 to 13.04 or any other release. It just does release-internal upgrades like from 12.04.1 to 12.04.2 to 12.04.3 - which is almost always what we want.

The first thing I do on a new system is:
* apt-get purge nano - don't want that crap. vi all the way.
* push my desktop ssh keys over - ssh-copy-id
* install a few other packages to make it fit into my network better.  A few core packages on my desktop/server systems:
    - openssh-server
    - postfix - satellite system only.
    - fail2ban / denyhosts
    - saidar
    - rsync
    - rdiff-backup
    - locate
    - git
    - lshw
    - ntp
    - monitoring software (cacti, SysUsage, monit, whatever you like).
    - log software - logwatch or splunk to make it easier to watch

Consistent installs are important. Consistent configurations to leverage other capabilities on the network are nice to have as well.  I use **ansible** to manage server setups, but a bash script that gets used over and over can work fine too.

I bet there are other things that I'm missing - pulled the software list from my current ansible common rule. Every server is a little different, however. I can't wait to see what others do.

---

