---
title: "adobe flash instalation"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by angelgabrielle8 on 2013-12-11
keep trying to insrall adobe flash o gnome ubuntu 12.4....just updated. First of all my terminal seems to have disappeared from the top with the links from before.. But found it on the keyboard. I keep getting this.What can I do please?
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,946 B of archives.
After this operation, 139 kB of additional disk space will be used.
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/multiverse flashplugin-installer i386 11.2.202.327ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse flashplugin-installer i386 11.2.202.327ubuntu0.12.04.1
  404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.327ubuntu0.12.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.327ubuntu0.12.04.1_i386.deb)  404  Not Found [IP: 91.189.92.184 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
nopassword@eeepc:~$ password
password: command not found
nopassword@eeepc:~$ password
password: command not found
nopassword@eeepc:~$ 
nopassword@eeepc:~$ password
password: command not found
nopassword@eeepc:~$ password
password: command not found
nopassword@eeepc:~$

---

### Post by deadflowr on 2013-12-11
password isn't a command.
a command is something you make the computer do, like upgrade or install packages.
first run a command like
```
sudo apt-get update
```
then, since you would be asking the command to run with root rights(sudo), it'll ask for a password.
Note that password field in the terminal are blank, type it as you remember it.

---

