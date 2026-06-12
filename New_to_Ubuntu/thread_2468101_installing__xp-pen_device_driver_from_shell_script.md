---
title: "installing  xp-pen device driver from shell script"
date: 2021-10-18
forum: New to Ubuntu
---

### Post by nginmu on 2021-10-18
I have an xp-pen artist 12 drawing tablet which claims compatibility with ubuntu  The manufacturer provides three linux drivers for the device two of which list ubuntu:  Ubuntu&#12289;Centos&#12289;Fedora&#12289;Red Hat&#12289;Manjaro&#12289;Arch&#12289;Debian&#12289;OpenSUSE&#12289;elementary OS&#12289;Mint&#12289;ezgo Linux&#12289;Pop!_OS&#12289;Mageia XP-PEN-pentablet-3.2.0.210824-1.x86_64.tar.gz  Ubuntu&#12289;Debian&#12289;elementary OS&#12289;Mint&#12289;ezgo Linux&#12289;Pop!_OS XP-PEN-pentablet-3.2.0.210824-1.x86_64.deb  Centos&#12289;Fedora&#12289;Red Hat&#12289;OpenSUSE&#12289;Mageia XP-PEN-pentablet-3.2.0.210824-1.x86_64.rpm  I downloaded XP-PEN-pentablet-3.2.0.210824-1.x86_64.tar.gz  When I open it with ark, it contains 3 items: directory 'App' install.sh uninstall.sh  I tried to run install.sh and got;  ```
 me@me-pc:~/Desktop/xp-pen-pentablet-3.2.0.210824-1.x86_64$ chmod +x install.sh me@me-pc:~/Desktop/xp-pen-pentablet-3.2.0.210824-1.x86_64$ ./install.sh /home/me/Desktop/xp-pen-pentablet-3.2.0.210824-1.x86_64/. cp: cannot create regular file '/lib/udev/rules.d/10-xp-pen.rules': Permission denied cp: cannot create directory '/usr/lib/pentablet': Permission denied can not find start script 
```  Now I'm lost. Can anyone give me any pointers?  This is the full install script:  [code] #! /bin/bash  # cd to current path dirname=`dirname $0` tmp="${dirname#?}" if [ "${dirname%$tmp}" != "/" ]; then 	dirname=$PWD/$dirname fi echo $dirname cd "$dirname"  # close driver if it running AppName=pentablet AppDir=pentablet pid=`ps -e|grep $AppName` appScript=$AppName".sh" if [ -n "$pid" ]; then 	echo $pid 	arr=() 	while read -r line; do 	   arr+=("$line") 	done

---

### Post by deadflowr on 2021-10-18
Preface it with sudo
```
me@me-pc:~/Desktop/xp-pen-pentablet-3.2.0.210824-1.x86_64$ **sudo** ./install.sh
```
Or run as root.
You need to use sudo or be root in order to do the write to the directories listed.

---

### Post by nginmu on 2021-10-18
Thanks I'll try.  edit.. thanks, it worked a treat. I feel stupid ;-)

---

