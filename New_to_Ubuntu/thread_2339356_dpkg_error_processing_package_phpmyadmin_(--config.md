---
title: "dpkg: error processing package phpmyadmin (--configure):  dependency problems - leavi"
date: 2016-10-07
forum: New to Ubuntu
---

### Post by kumar1432 on 2016-10-07
$ sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phpmyadmin is already the newest version (4:4.5.4.1-2ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up dbconfig-common (2.0.4ubuntu1) ...
dpkg: error processing package dbconfig-common (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of dbconfig-mysql:
 dbconfig-mysql depends on dbconfig-common (= 2.0.4ubuntu1); however:
  Package dbconfig-common is not configured yet.


dpkg: error processing package dbconfig-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on dbconfig-mysql | dbconfig-no-thanks | dbconfig-common (<< 2.0.0); however:
  Package dbconfig-mysql is not configured yet.
  Package dbconfig-no-thanks is not installed.
  Version of dbconfig-common on system is 2.0.4ubuntu1.


dpkg: error processing package phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbconfig-common
 dbconfig-mysql
 phpmyadmin
^[[AE: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2016-10-07
kumar1432l Hello; Welcome to the forum.

I will start the ball rolling, even though I may not be the best person in this case.
the report :
> 
| dbconfig-common (<< 2.0.0); however:

says that "dbconfig-common" must be strictly less than version 2.0.0 in order to install ... BUT
a higher version is installed:
> 
Version of dbconfig-common on system is 2.0.4ubuntu1.

Which is the correct version :
> 
 dbconfig-common (source: dbconfig-common): framework that helps packages to manage databases. In component main, is optional. Version 2.0.4ubuntu1 (xenial), package size 568 kB, installed size 1403 kB

So, that begs the question .. what is holding the package to that old version ?

Do we get any hints from:
```

apt-cache policy dbconfig-common

```

[INDENT][INDENT]gotta make the package manager happy
[/INDENT][/INDENT]

---

### Post by sisco311 on 2016-10-07
Please don't start multiple threads on the same topic.

Jailed the other thread. Moved this one to *New to Ubuntu* forum.

---

### Post by kumar1432 on 2016-10-07
out put for [COLOR=#000000][FONT=&quot]apt-cache policy dbconfig-common :
[/FONT][/COLOR]$ apt-cache policy dbconfig-common
dbconfig-common:
  Installed: 2.0.4ubuntu1
  Candidate: 2.0.4ubuntu1
  Version table:
 *** 2.0.4ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 Packages
        100 /var/lib/dpkg/status

---

### Post by Bashing-om on 2016-10-07
kumar1432l Well ....

That was a false trail .
How about any hints:
```

apt-cache policy dbconfig-mysql dbconfig-no-thanks

```
Please place the outputs between code tags to maintain readability:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


Looking to find what it will take to configure phpmyadmin .

[INDENT][INDENT]the answer
[INDENT][INDENT][INDENT]still blowing in the wind
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kumar1432 on 2016-10-07
out put for [COLOR=#000000][FONT=&quot]apt-cache policy dbconfig-mysql dbconfig-no-thanks:
[/FONT][/COLOR]$ apt-cache policy dbconfig-mysql dbconfig-no-thanks
dbconfig-mysql:
  Installed: 2.0.4ubuntu1
  Candidate: 2.0.4ubuntu1
  Version table:
 *** 2.0.4ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 Packages
        100 /var/lib/dpkg/status
dbconfig-no-thanks:
  Installed: (none)
  Candidate: 2.0.4ubuntu1
  Version table:
     2.0.4ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 Packages

---

### Post by Bashing-om on 2016-10-07
kumar1432l Welp ...

I am finding that the system is misleading us !
System says :
> 
phpmyadmin is already the newest version (4:4.5.4.1-2ubuntu1).

BUT there is a later version :
> 
Package phpmyadmin

xenial-updates (web): MySQL web administration tool [universe] 
4:4.5.4.1-2ubuntu2: all


Now, we must inquire if this system is fully updated ?
what results:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```

[INDENT][INDENT]are we there yet ?
[/INDENT][/INDENT]

---

### Post by kumar1432 on 2016-10-07
out put for [COLOR=#000000][FONT=&quot]sudo apt update[/FONT][/COLOR]
sudo apt upgrade
sudo apt -f install$ sudo apt update
[sudo] password for keshu: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
**keshu@techbox**:**~**$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up dbconfig-common (2.0.4ubuntu1) ...
dpkg: error processing package dbconfig-common (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of dbconfig-mysql:
 dbconfig-mysql depends on dbconfig-common (= 2.0.4ubuntu1); however:
  Package dbconfig-common is not configured yet.


dpkg: error processing package dbconfig-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on dbconfig-mysql | dbconfig-no-thanks | dbconfig-common (<< 2.0.0); however:
  Package dbconfig-mysql is not configured yet.
  Package dbconfig-no-thanks is not installed.
  Version of dbconfig-common on system is 2.0.4ubuntu1.


dpkg: error processing package phpmyadmin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 dbconfig-common
 dbconfig-mysql
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
**keshu@techbox**:**~**$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up dbconfig-common (2.0.4ubuntu1) ...
dpkg: error processing package dbconfig-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of dbconfig-mysql:
 dbconfig-mysql depends on dbconfig-common (= 2.0.4ubuntu1); however:
  Package dbconfig-common is not configured yet.


dpkg: error processing package dbconfig-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on dbconfig-mysql | dbconfig-no-thanks | dbconfig-common (<< 2.0.0); however:
  Package dbconfig-mysql is not configured yet.
  Package dbconfig-no-thanks is not installed.
  Version of dbconfig-common on system is 2.0.4ubuntu1.


dpkg: error processing package phpmyadmin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 dbconfig-common
 dbconfig-mysql
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2016-10-07
kumar1432; Yuk ...

unpleasant surprise and got me spinning my wheels .

OK.
Any joy :
```

sudo dpkg-reconfigure dbconfig-mysql

```
and we see what the package manager advises ?

[INDENT][INDENT]gotta be a way forward
[/INDENT][/INDENT]

---

### Post by kumar1432 on 2016-10-07
> **Bashing-om said:**
> kumar1432; Yuk ...

unpleasant surprise and got me spinning my wheels .

OK.
Any joy :
```

sudo dpkg-reconfigure dbconfig-mysql

```
and we see what the package manager advises ?
[INDENT][INDENT]gotta be a way forward
[/INDENT]
[/INDENT]

sudo dpkg-reconfigure dbconfig-mysql
[sudo] password for keshu: 
/usr/sbin/dpkg-reconfigure: dbconfig-mysql is broken or not fully installed

---

### Post by Bashing-om on 2016-10-07
kumar1432; Well ..

can we push it just a bit ?
```

sudo apt install --reinstall dbconfig-mysql 

```

[INDENT][INDENT]maybe Yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kumar1432 on 2016-10-07
> **Bashing-om said:**
> kumar1432; Well ..

can we push it just a bit ?
```

sudo apt install --reinstall dbconfig-mysql 

```
[INDENT][INDENT]maybe Yes[INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

sudo apt install --reinstall dbconfig-mysql
[sudo] password for keshu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for dbconfig-mysql:amd64

---

### Post by Bashing-om on 2016-10-07
kumar1432; Hummm ...

Push a bit harder:
```

sudo apt install dbconfig-mysql

```

[INDENT][INDENT]how now
[/INDENT][/INDENT]

---

### Post by kumar1432 on 2016-10-07
> **Bashing-om said:**
> kumar1432; Hummm ...

Push a bit harder:
```

sudo apt install dbconfig-mysql

```
[INDENT][INDENT]how now
[/INDENT]
[/INDENT]

it shows same ... error ...
$ sudo apt install dbconfig-mysql
[sudo] password for keshu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dbconfig-mysql is already the newest version (2.0.4ubuntu1).
dbconfig-mysql set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up dbconfig-common (2.0.4ubuntu1) ...
dpkg: error processing package dbconfig-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of dbconfig-mysql:
 dbconfig-mysql depends on dbconfig-common (= 2.0.4ubuntu1); however:
  Package dbconfig-common is not configured yet.


dpkg: error processing package dbconfig-mysql (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on dbconfig-mysql | dbconfig-no-thanks | dbconfig-common (<< 2.0.0); however:
  Package dbconfig-mysql is not configured yet.
  Package dbconfig-no-thanks is not installed.
  Version of dbconfig-common on system is 2.0.4ubuntu1.


dpkg: error processing package phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbconfig-common
 dbconfig-mysql
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2016-10-07
kumar1432; Yuk .

Spinning my wheels again . I will have to re-think this and look at the dependencies .

[INDENT]study twice
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-10-08
kumar1432l Yeah !

My logic from "phpmyadmin depends on dbconfig-mysql | dbconfig-no-thanks | dbconfig-common (<< 2.0.0); : is valid that the dependency for phpmyadmin depends on dbconfig-mysql -or- dbconfig-no-thanks -or- dbconfig-common (<< 2.0.0) . So we only want ONE of the three installed.

so, what is currently installed ?
```

dpkg -l dbconfig-mysql dbconfig-no-thanks dbconfig-common 

```
Yeah, we already know that the system reports  " Package dbconfig-no-thanks is not installed." Let's double check .... and consider removing the dbconfig-common package .

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by kumar1432 on 2016-10-08
> **Bashing-om said:**
> kumar1432l Yeah !

My logic from "phpmyadmin depends on dbconfig-mysql | dbconfig-no-thanks | dbconfig-common (<< 2.0.0); : is valid that the dependency for phpmyadmin depends on dbconfig-mysql -or- dbconfig-no-thanks -or- dbconfig-common (<< 2.0.0) . So we only want ONE of the three installed.

so, what is currently installed ?
```

dpkg -l dbconfig-mysql dbconfig-no-thanks dbconfig-common 

```
Yeah, we already know that the system reports  " Package dbconfig-no-thanks is not installed." Let's double check .... and consider removing the dbconfig-common package .
[INDENT][INDENT]maybe yes ?
[/INDENT]
[/INDENT]

$ dpkg -l dbconfig-mysql dbconfig-no-thanks dbconfig-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iF  dbconfig-commo 2.0.4ubuntu1 all          framework that helps packages to 
iU  dbconfig-mysql 2.0.4ubuntu1 all          dbconfig-common MySQL/MariaDB sup
un  dbconfig-no-th <none>       <none>       (no description available)

---

### Post by Bashing-om on 2016-10-08
kumar1432; OK !

Now we are making forward progress !
```

sudo apt purge dbconfig-common
sudo apt install --reinstall dbconfig-mysql
sudo dpkg-reconfigure phpmyadmin

```

Now maybe
[INDENT][INDENT][INDENT]yes
[/INDENT][/INDENT][/INDENT]

---

### Post by kumar1432 on 2016-10-08
> **Bashing-om said:**
> kumar1432; OK !

Now we are making forward progress !
```

sudo apt purge dbconfig-common
sudo apt install --reinstall dbconfig-mysql
sudo dpkg-reconfigure phpmyadmin

```

Now maybe[INDENT][INDENT][INDENT]yes
[/INDENT]
[/INDENT]
[/INDENT]

after using sudo purge dbconfig-common & sudp apt install --reinstall dbconfig-mysql
when i use sudo dpkg-reconfigure phpmyadmin 
output:
$ sudo dpkg-reconfigure phpmyadmin
/usr/sbin/dpkg-reconfigure: phpmyadmin is broken or not fully installed

---

### Post by Bashing-om on 2016-10-08
kumar1432; K;

Let's try this again now :
```

sudo apt install --reinstall phpmyadmin

```

If it turns out that the package is broken we see if we can remove it to re-install ??

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT]do something else
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kumar1432 on 2016-10-08
> **Bashing-om said:**
> kumar1432; K;

Let's try this again now :
```

sudo apt install --reinstall phpmyadmin

```

If it turns out that the package is broken we see if we can remove it to re-install ??
[INDENT][INDENT]if at 1st you do not succeed[INDENT][INDENT]do something else
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

same error is coming out..

---

### Post by Bashing-om on 2016-10-08
kumar1432; well, shucks .

Will the package manager allow us to remove phpmyadmin ? If so  we try a fresh install.
```

sudo apt purge phpmyadmin

```
If you have made up particular config files. save the files prior to purging .

[INDENT][INDENT]try try try again
[/INDENT][/INDENT]

---

