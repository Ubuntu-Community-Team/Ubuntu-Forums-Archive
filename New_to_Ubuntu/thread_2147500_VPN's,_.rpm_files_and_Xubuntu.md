---
title: "VPN's, .rpm files and Xubuntu"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by China Diapers on 2013-05-22
I am considering coming back to Xubuntu after a horrid two years off with the putrid MS Windows. 


There a few things causing me to hesitate, the main one being I regularly work from home now so need to log into my works network remotely. The techies have sent me an .rpm file to install to enable me to get the VPN up and running. Will .rpm files work with Xubuntu? I thought these were Red Hat/Fedora files? Has anybody here done anything like this before?


Thanks


Adrian

---

### Post by monkeybrain2012 on 2013-05-22
You can try using alien to convert the rpm to deb. You can find it in the repo. Mind you, it doesn't always work, but works for me on a few rare occasions.

[http://taufanlubis.wordpress.com/2008/01/22/alien-%E2%80%93-convert-rpm-to-deb-or-deb-to-rpm/](http://taufanlubis.wordpress.com/2008/01/22/alien-%E2%80%93-convert-rpm-to-deb-or-deb-to-rpm/)

Failing that you may ask them for a tarball, they probably can give you one.

---

### Post by Lars Noodén on 2013-05-22
In addition to trying alien, you might try searching the repositories for the same package.  If it's not in the Ubuntu repositories, the vendor might have their own you could use.

---

### Post by China Diapers on 2013-05-22
Thanks guys, will give all those ideas a go and report back with my results

---

### Post by China Diapers on 2013-05-22
OK spoke to the techies and the VPN is provided by Juniper and a quick Google search brings me back to this very forum:

[http://ubuntuforums.org/showthread.php?t=2067521](http://ubuntuforums.org/showthread.php?t=2067521)

---

### Post by deadflowr on 2013-05-22
Alien conversion of rpm packages works best for the most generic, basic of packages.

The more complex the package build, the more likely it'll fail to convert.

In most instances, if a deb version of a package you want doesn't exist, building it from source is the better option.

---

### Post by China Diapers on 2013-05-22
Came across this on the Juniper website:

[http://kb.juniper.net/InfoCenter/index?page=content&id=KB21175&actp=RSS](http://kb.juniper.net/InfoCenter/index?page=content&id=KB21175&actp=RSS)

---

### Post by China Diapers on 2013-05-25
OK so I got the VPN working OK, can ping my work machine but getting the below error when trying to log in to the machine using Remmina:

> Failed to startup SSH session: connection refused

Entered below details:

Connection name: *****
Group:blank
Protocol: RDP
Server: *******
User name[I]: *****
[/I]Password[I]: *****
[/I]Domain: blank
Resolution: User client resolution
Colour Depth: 256

Any ideas?

---

### Post by China Diapers on 2013-05-26
Sorted, navigated to advanced tab in  Remote Desktop Preferences and choose RDP in Security drop down menu and saved

---

### Post by RoyBinder1972 on 2013-05-26
dont use remmina - use nautilus-connect-to-server (the ssh option)
or (the best way) open your terminal and print " ssh username@yourIPaddress "

---

### Post by China Diapers on 2013-05-27
Will give it a go, thx

---

