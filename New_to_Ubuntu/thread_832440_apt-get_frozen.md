---
title: "apt-get frozen"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by hive225 on 2008-06-17
I tried installing vsftpd and I got:
```
$ sudo apt-get -f install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vsftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up vsftpd (2.0.6-1ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing vsftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now no matter what I do with apt-get it spits that message out. Someone please help!

---

### Post by aktiwers on 2008-06-17
Have you tried:
```
sudo apt-get -f install
```
```
sudo apt-get update
```

---

### Post by wormser on 2008-06-17
There is no need for the -f. The f switch is for fixing broken.  Try this.

```
sudo apt-get install vsftpd
```More on the f switch from the man page.

>    -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system´s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect(8) or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations. Configuration Item: APT::Get::Fix-Broken.

---

### Post by hive225 on 2008-06-17
```
$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vsftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up vsftpd (2.0.6-1ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing vsftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up vsftpd (2.0.6-1ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing vsftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

nothing I have tried has worked

---

### Post by avtolle on 2008-06-17
Suggestion: try cleaning the cache by```
sudo apt-get clean
``` then give it another try.

---

### Post by hive225 on 2008-06-17
```

$ sudo apt-get clean
$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vsftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up vsftpd (2.0.6-1ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing vsftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

nope

---

### Post by wormser on 2008-06-17
> **hive225 said:**
> 1 not fully installed or removed.

It looks like the package partially installed from your original command and is now causing the issue.  I am not sure which of the following commands will work but one of them should.  Try one then try installing again with the command I posted earlier.  Please post which one works.

```
sudo apt-get purge vsftpd
``````
sudo apt-get autoremove
``````
sudo apt-get autoclean
```

---

### Post by hive225 on 2008-06-17
None of them worked. I finally tried all 3 after the other and still got the same result.

```

$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
```

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```
```

$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  vsftpd
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/96.8kB of archives.
After this operation, 401kB of additional disk space will be used.
Selecting previously deselected package vsftpd.
(Reading database ... 20174 files and directories currently installed.)
Unpacking vsftpd (from .../vsftpd_2.0.6-1ubuntu1_i386.deb) ...
Setting up vsftpd (2.0.6-1ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing vsftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by wormser on 2008-06-17
I did not see the purge command in your post.

```
sudo apt-get purge vsftpd
```

There are some options with the command dpkg that might work.

---

### Post by hive225 on 2008-06-17
I executed the command, I just forgot to post it (and the result).

Here it is right before the other commands were executed:
```
$ sudo apt-get purge vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vsftpd*
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 401kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 20225 files and directories currently installed.)
Removing vsftpd ...
 * Stopping FTP server: vsftpd
No /usr/sbin/vsftpd found running; none killed.
   ...done.
Purging configuration files for vsftpd ...

```

I still have no idea what to do!

---

### Post by wormser on 2008-06-17
I found this potential resolution in another forum.  I recall seeing this fix similar issues before.

> After you get that error, try apt-get -f install to force an install of the files that didn't get loaded because of the error. Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.

So, repeat these 2 commands until it is fixed.

```
sudo apt-get -f install
```
```
sudo apt-get upgrade
```

---

### Post by wormser on 2008-06-17
If that is not working try the following.  It might need to be repeated a few times.

```
sudo dpkg --configure -a
```

---

### Post by cariboo on 2008-06-17
It looks like there is a bug in the installation script. Have you tried just downloading the file and using dpkg to install it to see if you get the same error message.

Jim

---

### Post by fortran01 on 2008-11-05
It's a bug of sysv-rc component update-rc.d

I have to aptitude purge sysv-rc. It will prompt for a downgrade. Downgrade and then reinstall the offended packages.

---

