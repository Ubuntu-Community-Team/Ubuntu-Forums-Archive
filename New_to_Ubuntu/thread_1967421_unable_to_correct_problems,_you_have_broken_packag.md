---
title: "unable to correct problems, you have broken packages"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-04-28
Hi All
I am trying to install mysql on my 11.10 acer. I read the man page on installing mysql:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
and so I entered:
```

glenn@acer:~$ sudo apt-get install mysql-client-core-5.1 mysql-cluster-client-5.1
[sudo] password for glenn: 

```which generated the following output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 mysql-client-core-5.1 : Depends: libmysqlclient16 (>= 5.1.62-0ubuntu0.11.10.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```Ok, broken packages, no problem:
```

glenn@acer:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```Hang on, didn't you just say I had broken packages?
So I try to install mysql again. I get this error message:
```

...
The following packages have unmet dependencies:
 mysql-client-core-5.1 : Depends: libmysqlclient16 (>= 5.1.62-0ubuntu0.11.10.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```I thought -f fixed broken package?

---

### Post by plucky on 2012-04-28
This is what I got when I tried that install ```
 sudo apt-get install mysql-client-core-5.1 mysql-cluster-client-5.1
[sudo] password for ******: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 mysql-client-core-5.1 : Depends: libmysqlclient16 (>= 5.1.62-0ubuntu0.11.10.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Then I tried ```
sudo apt-get install libmysqlclient16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**libmysqlclient16 is already the newest version.**
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libxcomposite1:i386 nspluginwrapper libnspr4-0d:i386
  libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386
  libxinerama1:i386 nspluginviewer:i386 libxft2:i386 libthai0:i386
  libjasper1:i386 libpango1.0-0:i386 libxcb-render0:i386 libxcursor1:i386
  libxcb-shm0:i386 libxrandr2:i386 libnss3-1d:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Then I ran ```
sudo apt-get install mysql-client-core-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libxcomposite1:i386 nspluginwrapper libnspr4-0d:i386
  libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386
  libxinerama1:i386 nspluginviewer:i386 libxft2:i386 libthai0:i386
  libjasper1:i386 libpango1.0-0:i386 libxcb-render0:i386 libxcursor1:i386
  libxcb-shm0:i386 libxrandr2:i386 libnss3-1d:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  mysql-client-core-5.1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 99.4 kB of archives.
After this operation, 365 kB of additional disk space will be used.
Get:1 http://mirror01.th.ifl.net/ubuntu/ oneiric-updates/main mysql-client-core-5.1 amd64 5.1.62-0ubuntu0.11.10.1 [99.4 kB]
Fetched 99.4 kB in 0s (262 kB/s)           
Selecting previously deselected package mysql-client-core-5.1.
(Reading database ... 288757 files and directories currently installed.)
Unpacking mysql-client-core-5.1 (from .../mysql-client-core-5.1_5.1.62-0ubuntu0.11.10.1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mysql-client-core-5.1 (5.1.62-0ubuntu0.11.10.1) ...
```

And as that ran I did ```
sudo apt-get install mysql-cluster-client-5.1Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libatk1.0-0:i386 libxcomposite1:i386 nspluginwrapper libnspr4-0d:i386
  libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386 libpixman-1-0:i386
  libxinerama1:i386 nspluginviewer:i386 libxft2:i386 libthai0:i386
  libjasper1:i386 libpango1.0-0:i386 libxcb-render0:i386 libxcursor1:i386
  libxcb-shm0:i386 libxrandr2:i386 libnss3-1d:i386 libgtk2.0-0:i386
Use 'apt-get autoremove' to remove them.
Suggested packages:
  libdbi-perl libdbd-mysql-perl
The following packages will be REMOVED
  libmysqlclient16 libqt4-sql-mysql mysql-client-core-5.1
The following NEW packages will be installed
  mysql-cluster-client-5.1
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 4,299 kB of archives.
After this operation, 5,251 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://mirror01.th.ifl.net/ubuntu/ oneiric/universe mysql-cluster-client-5.1 amd64 7.1.9a-0ubuntu2 [4,299 kB]
Fetched 4,299 kB in 6s (626 kB/s)                                              
(Reading database ... 288763 files and directories currently installed.)
Removing mysql-client-core-5.1 ...
Removing libqt4-sql-mysql ...
Removing libmysqlclient16 ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package mysql-cluster-client-5.1.
(Reading database ... 288744 files and directories currently installed.)
Unpacking mysql-cluster-client-5.1 (from .../mysql-cluster-client-5.1_7.1.9a-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up mysql-cluster-client-5.1 (7.1.9a-0ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

Why the first command didn't work I don't really know.

So Try the commands individually and see if it works for you

Good Luck

---

### Post by Senior_Buckethead on 2012-04-28
Thanks for the help,

I installed libmysqlclient16, then installed mysql-client-core-5.1, then mysql-cluster-client-5.1.
Libmysqlclient16 installed ok, and mysql-client-core-5.1, but when I installed mysql-cluster-client-5.1, it removed mysql-client-core-5.1.
Same if I installed mysql-cluster-client-5.1, it would uninstall mysql-client-core-5.1.

And, when I tested by typing mysql, it told me that it was not installed!!!

So I opened synaptic and installed it that way.

---

