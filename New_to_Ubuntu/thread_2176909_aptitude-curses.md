---
title: "aptitude-curses"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by Richard_J_Lisanti on 2013-09-26
sudo apt-get upgrade always produces: "update-alternatives: error: cannot stat file '/usr/bin/aptitude-curses': Input/output error".  I turns out that the files in questions looks like this:

rwxr-xr-x  1 root     root         5106 Jan 11  2013 apt-clone
-rwxr-xr-x  1 root     root        18992 Sep  7 23:26 apt-config
-rwxr-xr-x  1 root     root         1038 Mar 26  2013 aptdcon
-rwxr-xr-x  1 root     root        23264 Sep  7 23:26 apt-extracttemplates
-rwxr-xr-x  1 root     root       204560 Sep  7 23:26 apt-ftparchive
-rwxr-xr-x  1 root     root       192592 Sep  7 23:26 apt-get
-rwxr-xr-x  1 root     root        23160 Sep  7 23:26 apt-internal-solver
**lrwxrwxrwx  1 root     root           26 Jan  5  2013 aptitude -> /etc/alternatives/aptitude**
-rwxr-xr-x  1 root     root         1939 Apr 18 19:56 aptitude-create-state-bundle
**-?????????  ? ?        ?               ?            ? aptitude-curses**
-rwxr-xr-x  1 root     root         2850 Apr 18 19:56 aptitude-run-state-bundle
-rwxr-xr-x  1 root     root         8067 Sep  7 23:24 apt-key
-rwxr-xr-x  1 root     root        43784 Sep  7 23:26 apt-mark

This error prevents apt-get purges, updates, autoremove etc.   Also the link which points back to aptitude-curses says it's broken.   I tried deleting packages from /var/lib/dpkg/status with no luck.  For example, firefox attemped update yields (sudo apt-get upgrade) :

[B]Setting up firefox (24.0+build1-0ubuntu0.12.04.1) ...
update-alternatives: error: cannot stat file '/usr/bin/aptitude-curses': Input/output error
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
[/B]
Is there a way to re-create this file (or put some dummy stuff in it)?   P.S. I don't think you can rm, touch, etc. the aptitude-curses file as it is undefined.

Please help...:(:(

---

### Post by Kirboosy on 2013-09-26
Welcome to the forums! :D

Looks like you have a permissions issue. Please open a terminal and try the following commands seperately.
```
sudo chmod 751 /usr/bin/aptitude-curses
```
```
sudo chown root:root /usr/bin/aptitude-curses
```

See if that changes anything.

Hope that helps!
~Caboose
PS. Please use [CODE] tags when pasting code. Under the advanced editor its the **#** symbol. This will make code reading more distinguished and easier to read. Thanks!

---

### Post by Richard_J_Lisanti on 2013-09-26
Sorry, sudo chown root:root and sudo chmod 751 on file aptitude-curses both yield the same message:
**cannot access `/usr/bin/aptitude-curses': Input/output error**

Notice the link 
**aptitude -> /etc/alternatives/aptitude** if one follows this link as follows:
# cd /etc/alternatives
# ls -la|grep apt  
**lrwxrwxrwx   1 root root    24 Jan  5  2013 aptitude -> /usr/bin/aptitude-curses**
lrwxrwxrwx   1 root root    40 Jan  5  2013 aptitude.8.gz -> /usr/share/man/man8/aptitude-curses.8.gz
lrwxrwxrwx   1 root root    43 Jan  5  2013 aptitude.cs.8.gz -> /usr/share/man/cs/man8/aptitude-curses.8.gz
lrwxrwxrwx   1 root root    43 Jan  5  2013 aptitude.de.8.gz -> /usr/share/man/de/man8/aptitude-curses.8.gz
lrwxrwxrwx   1 root root    43 Jan  5  2013 aptitude.es.8.gz -> /usr/share/man/es/man8/aptitude-curses.8.gz
.
.
.
I think aptitude needs re-installation but I'm at a catch-22 since I can't install anything.  I noticed that if I do:
**# man aptitude-curses**
This takes me to the normal 'manual' entry for 'aptitude' which suggests that aptitude-curses was a bin file for the aptitude package manager.   I think this bug was introduced during an update of ubuntu 12.04 since a # uname -a yields:
**Linux m4a89gtd-Rich 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux** before then everything was working.   Most of the blogs for this type of error suggest things like [http://askubuntu.com/questions/252777/how-can-i-resolve-dpkg-dependency](http://askubuntu.com/questions/252777/how-can-i-resolve-dpkg-dependency)
I"ve tried all kinds dpkg and apt-get solutions as suggested by the blogs but to no avail.  The another question is why is apt-get trying to use aptitude which I thought was being phased out?  If I could get a copy of someone's aptitude-curses file, maybe I can break the links then re-establish the link to a different directory or something.  

Thanks for your time I know how precious it is.   (P.S. I'm an old-timer (retired) end-user but not a linux guru - I have a hard enough time just making my own system work for me.  However, I do regret going to 12.04 because I've had many issues that I didn't have in previous ubuntu versions. I do back up my home directory but from past experience it takes days or weeks to get to the same place you were before.)

---

