---
title: "Getting apache to run at boot"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-05-11
Okay, so I have apache installed and installed it from a tarball instead of using apt-get.  Still works just fine, except I'm not able to get it to start on boot.

So what I've done is make the following shell script and put it in /etc/init.d folder.  I named it apacheStart.sh

```
cd /usr/local/apache2/bin
sudo ./apachectl -k start
```

Then after that I put in a link to that file in /etc/rc2.d


But it didn't boot up.  What am I doing wrong?  This is the exact same process I type in bash to start apache manually.

---

### Post by scxtt on 2008-05-11
you can't (and don't need to) use sudo for something like that - when your box is booting up, it's doing everything as the root user ...

try putting:

/usr/local/apache2/bin/apachectl -k start

as a line in /etc/rc.local and then reboot.

---

### Post by CryptiniteDemon on 2008-05-11
There is no folder called rc.local in /etc

nevermind, it's a file.

---

### Post by scxtt on 2008-05-11
it's not a folder, it's a file ...
```
:> ls -l rc.local
-rwxr-xr-x 1 root root 547 Nov 30 23:19 rc.local
```

i have it in 7.10 - not sure if they did away w/ it in 8.04 :-\

---

### Post by spiderbatdad on 2008-05-11
also if you have installed apache2 then the command is apache2ctl start.

---

