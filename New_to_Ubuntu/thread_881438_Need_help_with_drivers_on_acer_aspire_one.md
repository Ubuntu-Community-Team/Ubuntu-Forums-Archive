---
title: "Need help with drivers on acer aspire one"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Dapman01 on 2008-08-06
Hi,
I'm using this [guide]("http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html") to help me install drivers, but when I get up to the part when I need to type "make" I get this error
make: *** No targets specified and no makefile found.  Stop.[LIST=1]
[/LIST]

---

### Post by Ryadt on 2008-08-06
Can you post the complete input/output of the terminal.

---

### Post by Dapman01 on 2008-08-06
Thanks for the reply

patrick@patrick-laptop:~$ sudo apt-get install build-essential
[sudo] password for patrick: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
patrick@patrick-laptop:~$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--00:45:06--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz.1'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [application/x-gzip]

100%[====================================>] 485           --.--K/s             

00:45:06 (12.47 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz.1' saved [485/485]

patrick@patrick-laptop:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
patrick@patrick-laptop:~$ cd madwifi-ng-r2756+ar5007
patrick@patrick-laptop:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.
patrick@patrick-laptop:~/madwifi-ng-r2756+ar5007$

---

### Post by kesman on 2008-08-06
Try to simply skip the part, I think there's a typo in the howto.
The next step seems to be
```

sudo make install

```

which makes more sense than just make.

---

### Post by Ryadt on 2008-08-06
The tutorial you are following is outdated and the driver you downloaded as well.

---

### Post by Ryadt on 2008-08-06
Try this tutorial
[http://ubuntuforums.org/showthread.php?t=795984&highlight=AR5007](http://ubuntuforums.org/showthread.php?t=795984&highlight=AR5007)

---

