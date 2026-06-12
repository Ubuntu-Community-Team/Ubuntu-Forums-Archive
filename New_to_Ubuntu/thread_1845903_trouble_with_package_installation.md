---
title: "trouble with package installation"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by stonecoldjha on 2011-09-18
Hello there!!!
I use ubuntu 10.04, and I was trying to install msttcorefonts. But the installation failed with the messages below:

[B]sonu@sonu-desktop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ttf-mscorefonts-installer instead of msttcorefonts
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  xscreensaver pcmanfm lxpanel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up ttf-mscorefonts-installer (3.2ubuntu0.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

how do i fix it??

---

### Post by debd on 2011-09-18
> [B]Note, selecting ttf-mscorefonts-installer instead of msttcorefonts
ttf-mscorefonts-installer is already the newest version.[/B]

its already indtalled.

---

### Post by sikander3786 on 2011-09-18
Try these command from the Terminal and post the outputs please:

```
sudo mv /var/cache/debconf/config.dat /var/cache/debconf/config.dat.bad
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get install msttcorefonts
```

---

### Post by stonecoldjha on 2011-09-18
Following is the terminal output of those commands:

[B]sonu@sonu-desktop:~$ sudo mv /var/cache/debconf/config.dat /var/cache/debconf/config.dat.bad
[sudo] password for sonu: 
sonu@sonu-desktop:~$ sudo dpkg --configure -a
Setting up ttf-mscorefonts-installer (3.2ubuntu0.1) ...
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
sonu@sonu-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xscreensaver pcmanfm lxpanel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
Setting up ttf-mscorefonts-installer (3.2ubuntu0.1) ...
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
sonu@sonu-desktop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ttf-mscorefonts-installer instead of msttcorefonts
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  xscreensaver pcmanfm lxpanel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
Setting up ttf-mscorefonts-installer (3.2ubuntu0.1) ...
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]sonu@sonu-desktop:~$

---

### Post by sikander3786 on 2011-09-18
Thanks for the outputs.

Now please run these commands one-by-one:

```
sudo mv /var/cache/debconf/passwords.dat /var/cache/debconf/passwords.dat.bad
sudo mv /var/cache/debconf/templates.dat /var/cache/debconf/templates.dat.bad
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get install msttcorefonts
```

---

