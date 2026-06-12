---
title: "can't find installed program"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by unibroker on 2012-06-12
I tried to install a program called sysstat from the command line using tar, configure, make and install.  But when I do a whereis or a locate it returns nothing.  Following the configure command the following code was returned.  ```
 Sysstat version:		10.0.5
   Installation prefix:		/usr/local
   rc directory:		/etc
   Init directory:		/etc/init.d
   Configuration directory:	/etc/sysconfig
   Man pages directory:		${datarootdir}/man
   Compiler:			gcc
   Compiler flags:		-g -O2

```

I also looked for it in DASH and Software Center but DASH couldn't find it and Software Center returned the program but an Install button as well.  Any ideas?

---

### Post by drmrgd on 2012-06-12
Locate might not be finding it because the database has not yet been refreshed.  I forget the frequency and interval that it follows.  You can always manually refresh it by:

```
sudo updatedb
```

Also, if you installed the binary in your normal $PATH, you could try the which command to find it:

```
which systat
```

Hope that helps.

---

### Post by unibroker on 2012-06-12
> **drmrgd said:**
> Locate might not be finding it because the database has not yet been refreshed.  I forget the frequency and interval that it follows.  You can always manually refresh it by:

```
sudo updatedb
```

Also, if you installed the binary in your normal $PATH, you could try the which command to find it:

```
which systat
```

Hope that helps.
Thanks for the response.  I did try to refresh the database with the code you suggested but I'm still coming up empty.  Before I posted I did a logout/login and then a shutdown and restart figuring the same thing as you but that did nothing either.

---

### Post by philinux on 2012-06-12
I think that should be 

```
which sysstat
``` Double SS

---

### Post by wojox on 2012-06-12
Try ```
which sar
```

EDIT: oh yeah philinux, spelling error.

---

### Post by philinux on 2012-06-12
> **wojox said:**
> Try ```
which sar
```

EDIT: oh yeah philinux, spelling error.

Indeed. 

```
The sysstat package contains the following system performance tools:
 - sar: collects and reports system activity information;
 - iostat: reports CPU utilization and disk I/O statistics;
 - mpstat: reports global and per-processor statistics;
 - pidstat: reports statistics for Linux tasks (processes);
 - sadf: displays data collected by sar in various formats.
```

This package is in the repos too. Version 10.0.3-1

---

### Post by unibroker on 2012-06-12
> **philinux said:**
> Indeed. 

```
The sysstat package contains the following system performance tools:
 - sar: collects and reports system activity information;
 - iostat: reports CPU utilization and disk I/O statistics;
 - mpstat: reports global and per-processor statistics;
 - pidstat: reports statistics for Linux tasks (processes);
 - sadf: displays data collected by sar in various formats.
```

This package is in the repos too. Version 10.0.3-1
I did find sar which leads me to believe that sysstat is filled with components that are distributed in various places in the filesystem?

---

### Post by philinux on 2012-06-12
> **unibroker said:**
> I did find sar which leads me to believe that sysstat is filled with components that are distributed in various places in the filesystem?

I prefer installing from the repos. Since you did a manual compile the tools will not be in the normal places I'm guessing.

Your first post says "Installation prefix: /usr/local"

Someone with compiling knowledge and of sysstat may have more info.

---

### Post by Frogs Hair on 2012-06-12
I installed this program from the software center and learned a little about the program using the man page.```
man sysstat
```

I discovered online that the following command was needed to view stats. ```
sar
``` 

When I ran this command permission to view the log was denied. I then used sudo and found the program was not configured. I also installed the graphical front end and that didn't work either.

I have found this site to be helpful with learning about cli based administrative programs an commands. There appears to be a learning curve with this program.
  

[http://control.cyberciti.biz/tips/?s=sysstat](http://control.cyberciti.biz/tips/?s=sysstat)

---

### Post by wojox on 2012-06-12
> **philinux said:**
> I think that should be 

```
which sysstat
``` Double SS

OP did you try the correct spelling? I saw this after I posted.

---

### Post by drmrgd on 2012-06-12
> **Frogs Hair said:**
> I installed this program from the software center and learned a little about the program using the man page.```
man sysstat
```

I discovered online that the following command was needed to view stats. ```
sar
``` 

When I ran this command permission to view the log was denied. I then used sudo and found the program was not configured. I also installed the graphical front end and that didn't work either.

I have found this site to be helpful with learning about cli based administrative programs an commands. There appears to be a learning curve with this program.
  

[http://control.cyberciti.biz/tips/?s=sysstat](http://control.cyberciti.biz/tips/?s=sysstat)

Yes, you're not kidding.  Out of curiosity I downloaded the tarball and compiled it to see how it works.  It looks like it installs to /usr/local/bin for the most part:

```
mkdir -p /usr/local/lib/sa
mkdir -p /var/log/sa
mkdir -p /usr/local/bin
mkdir -p /usr/local/share/doc/sysstat-10.0.5
mkdir -p /etc/sysconfig
install -m 755 sa1 /usr/local/lib/sa
install -m 755 sa2 /usr/local/lib/sa
install -m 755 sadc /usr/local/lib/sa
install -m 755 sar /usr/local/bin
install -m 755 sadf /usr/local/bin
install -m 755 iostat /usr/local/bin
install -m 755 mpstat /usr/local/bin
install -m 755 pidstat /usr/local/bin
install -m 755 nfsiostat /usr/local/bin
install -m 755 cifsiostat /usr/local/bin
install -m 644 sysstat.ioconf /etc/sysconfig
install -m 644 sysstat.sysconfig /etc/sysconfig/sysstat
install -m 644 CHANGES /usr/local/share/doc/sysstat-10.0.5
install -m 644 COPYING /usr/local/share/doc/sysstat-10.0.5
install -m 644 CREDITS /usr/local/share/doc/sysstat-10.0.5
install -m 644 README /usr/local/share/doc/sysstat-10.0.5
install -m 644 FAQ /usr/local/share/doc/sysstat-10.0.5
install -m 644 *.lsm /usr/local/share/doc/sysstat-10.0.5

```

But, I ran into the same errors as you when trying to run it.  There does not appear to be a sysstat binary (thanks for pointing my spelling error!), and there appears to be some messing and tweaking to get it working.

---

### Post by unibroker on 2012-06-12
> **drmrgd said:**
> Yes, you're not kidding.  Out of curiosity I downloaded the tarball and compiled it to see how it works.  It looks like it installs to /usr/local/bin for the most part:

```
mkdir -p /usr/local/lib/sa
mkdir -p /var/log/sa
mkdir -p /usr/local/bin
mkdir -p /usr/local/share/doc/sysstat-10.0.5
mkdir -p /etc/sysconfig
install -m 755 sa1 /usr/local/lib/sa
install -m 755 sa2 /usr/local/lib/sa
install -m 755 sadc /usr/local/lib/sa
install -m 755 sar /usr/local/bin
install -m 755 sadf /usr/local/bin
install -m 755 iostat /usr/local/bin
install -m 755 mpstat /usr/local/bin
install -m 755 pidstat /usr/local/bin
install -m 755 nfsiostat /usr/local/bin
install -m 755 cifsiostat /usr/local/bin
install -m 644 sysstat.ioconf /etc/sysconfig
install -m 644 sysstat.sysconfig /etc/sysconfig/sysstat
install -m 644 CHANGES /usr/local/share/doc/sysstat-10.0.5
install -m 644 COPYING /usr/local/share/doc/sysstat-10.0.5
install -m 644 CREDITS /usr/local/share/doc/sysstat-10.0.5
install -m 644 README /usr/local/share/doc/sysstat-10.0.5
install -m 644 FAQ /usr/local/share/doc/sysstat-10.0.5
install -m 644 *.lsm /usr/local/share/doc/sysstat-10.0.5

```

But, I ran into the same errors as you when trying to run it.  There does not appear to be a sysstat binary (thanks for pointing my spelling error!), and there appears to be some messing and tweaking to get it working.
Unbelievable respondents!  This was just an exercise in downloading and installing software using the command line.  The author of the book I'm using could have used a better example especially as an introduction.  Thanks for your assistance!

---

### Post by unibroker on 2012-06-12
Last thing; would it be preferred to state that the issue arose as part of a learning exercise in the OP?  I feel like I wasted your folks's time because it might have been assumed that I was in a bind.

---

