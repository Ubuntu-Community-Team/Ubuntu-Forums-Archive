---
title: "A bit of confusion on the packing tutorial"
date: 2007-08-06
forum: Packaging and Compiling Programs
---

### Post by fatsheep on 2007-08-06
I am trying to figure out how to build debian packages and I found a tutorial in the documentation on Ubuntu's website: [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/).  I downloaded the hello source package to ~/debian and then the command to create the base.tgz archive for the pbuilder chroot environment as instructed:

```
sudo pbuilder create --distribution feisty --othermirror "deb http://archive.ubuntu.com/ubuntu feisty universe multiverse"
```

I am in the ~/debian directory which contains the source package "hello" (and it's .dsc file).  When I run the command to build the binary package from the source package, here is what I get:

```
**fatsheep:~/debian$ sudo pbuilder build *.dsc**
W: /home/fatsheep/.pbuilderrc does not exist
I: using fakeroot in build.
pbuilder-buildpackage/amd64 $Id: pbuilder-buildpackage-funcs,v 1.32 2006/11/06 20:06:25 lool Exp $
$Id: pbuilder-buildpackage,v 1.127 2006/08/15 13:14:25 dancer Exp $

Current time: Mon Aug  6 13:25:12 EDT 2007
pbuilder-time-stamp: 1186421112
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
hostname: Unknown host

```

If I try to update pbuilder:

```
**fatsheep:~/debian$ sudo pbuilder update**
W: /home/fatsheep/.pbuilderrc does not exist
Upgrading for distribution feisty
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
hostname: Unknown host

```

Any ideas?  Also, should I be looking at a different manual?  I just want to know how to create a little debian package from a python or bash script for starters.

---

### Post by jnorthr on 2007-08-06
This may help you a little : [http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)
as i always found IBM tutorials clear, but this one [http://www.debian-administration.org/articles/336](http://www.debian-administration.org/articles/336) is better for a starter tutorial as is [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by fatsheep on 2007-08-06
> **jnorthr said:**
> This may help you a little : [http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)
as i always found IBM tutorials clear, but this one [http://www.debian-administration.org/articles/336](http://www.debian-administration.org/articles/336) is better for a starter tutorial as is [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

Well I ended up getting a debian binary package compiled using the Debian New Maintainers Guide, however, I would still like to know why pbuilder won't work.  Am I using it incorrectly?

---

### Post by fatsheep on 2007-08-07
It seems my hostname is "broken" in some way.  For example, when installing the man2html package I get a "hostname: Unknown host" error message as well (even though it does seem to install fine).  I ran some commands:

```

fatsheep:~$ hostname
fatsheep-desktop
fatsheep:~$ hostname -f
**hostname: Unknown host**
fatsheep:~$ dnsdomainname -v
**dnsdomainname: Unknown host**


```

(The -f option for the hostname command is supposed to display the FQDN)

Here are the contents of my /etc/hosts file:

```
127.0.0.1 localhost
127.0.1.1 fatsheep-desktop.fatsheep@example.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Any ideas?  The only thing I can think of is that I changed my DNS servers when I was trying to diagnose an FTP problem but would that cause this error?

---

### Post by fatsheep on 2007-08-09
I believe I have fixed this by reverting to a backup of the /etc/hosts file.  

My original /etc/hosts (that I presume caused the problem):

> 
127.0.0.1 localhost
127.0.1.1 [email]fatsheep-desktop.fatsheep@example.com[/email]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

My backup I reverted to (that I presume fixed the problem):

> 
127.0.0.1	localhost
127.0.1.1	fatsheep-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


---

