---
title: "Think I have &quot;path&quot; problems with my external HDD install"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-15
I put Ubuntu onto an external USB HDD and that went pretty well. It boots right up when I want it to anyway.

Now, I'm trying to install the Atheros driver "ALX" needed for wired Ethernet. I can get the "makefile" generated but when I run it, I get this:

```
Backup exists: Makefile.bk

Backup exists: Makefile.bk

Backup exists: drivers/net/ethernet/broadcom/Makefile.bk

Backup exists: drivers/net/ethernet/atheros/Makefile.bk

Backup exists: Makefile.bk

Backup exists: Makefile.bk

Backup exists: drivers/net/ethernet/broadcom/Makefile.bk

alan@alan-Satellite-C855:~/compat-wireless-2012-07-03-pc$ make

make -C /lib/modules/3.5.0-17-generic/build M=/home/alan/compat-wireless-2012-07-03-pc modules

make: *** /lib/modules/3.5.0-17-generic/build: No such file or directory.  Stop.

make: *** [modules] Error 2
alan@alan-Satellite-C855:~/compat-wireless-2012-07-03-pc$ 
```

I "think" the offending part of the makefile is the path's it uses but not too sure. The package I'm using is "compat-wireless-2012-07-03-pc.tar" and I extract it to it's own directory called "cd compat-wireless-2012-07-03-pc" in the home directory.

The steps I'm using in the terminal are:
```
cd compat-wireless-2012-07-03-pc
./scripts/driver-select alx
make
sudo make install
```

---

### Post by steeldriver on 2013-04-15
Did you remember to install the appropriate kernel headers package for your system?

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by alhefner on 2013-04-15
> **steeldriver said:**
> Did you remember to install the appropriate kernel headers package for your system?

```
sudo apt-get install linux-headers-$(uname -r)
```

Not sure what that means but, I did try this:

```
first tried:
alan@alan-Satellite-C855:~$ sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`

Result:
[sudo] password for alan:
 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package linux-headers-generic is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Unable to locate package build-essential
E: Package 'linux-headers-generic' has no installation candidate
E: Unable to locate package linux-headers-3.5.0-17-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-17-generic'
```

Next tried:

```
alan@alan-Satellite-C855:~$ sudo apt-get install linux-headers-$(uname -r)

Results:

Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Unable to locate package linux-headers-3.5.0-17-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-17-generic'
```

Hope this provides some insight.

---

### Post by alhefner on 2013-04-15
As it turns out, I did have "path" problems... of my own making! ](*,)](*,)](*,) It seems I overlooked a very important part of the process of installation on an external HDD and installed to a partition instead of the device. How it ever booted up that way, I haven't a clue! Anyway, problem is solved.

---

