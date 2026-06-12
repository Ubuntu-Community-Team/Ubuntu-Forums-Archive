---
title: "I have a question about packages."
date: 2008-10-14
forum: New to Ubuntu
---

### Post by opendevlite on 2008-10-14
1.) when i install a .deb file, how do i know if what were the packages installed? Synaptic does not show it from its "History" list.

2.) another question is that how do i determine if a package is not a part of the default source list in "Software Sources"?

default meaning no "Third-Party Software" Added.

Thanks

---

### Post by Pro-reason on 2008-10-14
1) You'll find them under &#8220;local or obsolete&#8221; in Synaptic.  (Assuming you're talking about installing .deb files without using APT repos.)

2) As far I understand it, the system makes no distinction between &#8220;default&#8221; and &#8220;non-default&#8221; sources.  It just sees sources.  No doubt, however, a simple bash script could scan the list and find the ones that are not from certain repositories.

---

### Post by eentonig on 2008-10-14
For each package you want to find out the info, you can do

[PHP]user@host:~$ **apt-cache policy** ubuntu-desktop
ubuntu-desktop:
  Installed: (none)
  Candidate: 1.102
  Version table:
     1.102 0
        500 http://be.archive.ubuntu.com hardy/main Packages[/PHP]

This will tell you if a package is installed.

To find dependencies (which programs does this package need) or reverse dependencies (Which programs need this package)

[PHP]user@host:~$ **apt-cache depends** apache2
apache2
 |Depends: apache2-mpm-worker
 |Depends: apache2-mpm-prefork
  Depends: apache2-mpm-event
user@host:~$ **apt-cache rdepends** apache2
apache2
Reverse Depends:
 |nagios2-common
    apache2-mpm-itk
    apache2-mpm-event
    apache2-mpm-prefork
    apache2-mpm-worker
 |mythweb
    apache2-mpm-itk
    apache2-mpm-event
    apache2-mpm-prefork
    apache2-mpm-worker
 |phpmyadmin
    apache2-mpm-itk
    apache2-mpm-event
    apache2-mpm-prefork
    apache2-mpm-worker
...[/PHP]

You can play with the other **apt-cache** options to find out even more.

---

### Post by opendevlite on 2008-10-14
bump for help

---

### Post by Pro-reason on 2008-10-14
> **opendevlite said:**
> bump for help

That's rather rude.  You've promptly been given two answers to your query, and you have ignored them.  We're not paid to give you tech support, you know.

---

### Post by jemate18 on 2008-10-14
> **opendevlite said:**
> 1.) when i install a .deb file, how do i know if what were the packages installed? Synaptic does not show it from its "History" list.

2.) another question is that how do i determine if a package is not a part of the default source list in "Software Sources"?

default meaning no "Third-Party Software" Added.

Thanks

> How to know the where packages installed in a deb file?
```
dpkg --listfiles yourpackage
``` or ```
dpkg -L yourpackage
``` This will list the files and directories associated with your installation.

> To know all installed packages
```
dpkg --get-selections
``` This will display all packages.

> To search for just a package installed
```
dpkg --get-selections | grep yourwishtofindCanUseRegex
```

To see all the list of Ubuntu software/packages visit
> [http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

or you can check out your sources.list at
```
cat /etc/apt/sources.list
``` You can see if third party is commented or not....

---

