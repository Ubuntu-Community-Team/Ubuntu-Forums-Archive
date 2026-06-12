---
title: "How to Oracle 10g.RC2 (10.2.0.1) | Ubuntu 9.04"
date: 2009-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by woozly on 2009-06-09
== Version ==
* Oracle 10g.RC2 (10.2.0.1)
* Ubuntu 9.04
== Installation Ubuntu ==
 
Oracle installation need system varss 
```
 
export ORACLE_BASE=/opt/oracle
export ORACLE_HOME=$ORACLE_BASE/product/10.2.0/Db_1
export ORACLE_SID=DB_1
export LD_LIBRARY_PATH=$ORACLE_HOME/lib

```
 
```
 
./runInstaller -ignoreSysPrereqs

```
 
* Oracleinstaller --> Java Version 10g.RC2 need Java 1.5.x
 
''Switch java version''
```
 
# apt-get install java-1.5
# update-alternatives --config java

``` 
 
* Necessary installed pakages
 
```
 
linux-headers
linux-sources
gcc
make
binutils
lesstif2
libc6
libstdc++5
libc6-dev
rpm
alien
 
libaio-0.3.103-3.i386.rpm 

```
 
RPM need softlink to /bin/rpm
```
 
# ln -s /bin/rpm /usr/sbin/rpm

```
 
Download, convert rpm to .deb and install libaio-0.3.103-3.i386.rpm
```
 
 
# alien libaio-0.3.103-3.i386.rpm
# dpkg -i libaio-0.3.103-3.i386.deb
# alien -d libaio-0.3.103-3.i386.rpm

```
 
After the installation ./ scripts as root
 
```
 
/opt/oracle/oraInventory/orainstRoot.sh
/opt/oracle/product/10.2.0/Db_1/root.sh

```
 
Error while exec the scripts 
```
 
/opt/oracle/product/10.2.0/Db_1/root.sh: 108: /bin/awk: not found
#ls -s /usr/bin/awk /bin/awk

```
 
/bin/chgrp: invalid group: `nobody'
#groupadd nobody
 
== '''FAQ''' ==
 
**'''Error:''' No protocol specified**
* Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
 
You're logged into the machine as one user (like pmarino) but you're trying to install as another user (like oracle).
Go to an xterm (or other terminal) where you're logged in as foo and type "sudo xhost +". 
This will allow anybody to open an X window on your monitor.
 
```
root@[foo_host]:/# xhost +
```
 
**'''Error:''' in shell box while run installer--> sh /bin/rpm not found**
 
STD ubuntu/debian installed rpm /usr/sbin
ln -s /bin/rpm /usr/sbin/rpm
 
**'''Error:''' rpm: To install rpm packages on Debian systems, use alien. See README.Debian.**
 
**'''Error:''' utilities ctx_on**
 
```
 
INFO: make: *** [/opt/oracle/product/10.2.0/Db_1/rdbms/lib/tg4pwd] Error 1
INFO: End output from spawned process.
INFO: ----------------------------------
INFO: Exception thrown from action: make
Exception Name: MakefileException
Exception String: Error in invoking target 'utilities ctx_on' of makefile '/opt/oracle/product/10.2.0/Db_1/rdbms/lib/ins_rdbms.mk'. 
See '/opt/oracle /oraInventory/logs/installActions2009-06-08_11-19-09PM.log' for details.
Exception Severity: 1
 

```
```
 
export LD_LIBRARY_PATH=$ORACLE_HOME/lib 
ln &shy;s /usr/bin/basename /bin/basename
ln &shy;s $ORACLE_HOME/lib/libclient10.a $ORACLE_HOME/lib/libagtsh.a
 
#$ORACLE_HOME/bin/genagtsh $ORACLE_HOME/lib/libagtsh.so 1.0
try: ./genagtsh

```
 
== NOTESSSS ! ==
'''find on web...other possible pakages'''
binutils
libdb2
libdb3
libdb4.1
libdb1-compat
cpp-3.3
gcc-3.3
libstdc++5-3.3-dev
libstdc++2.10-glibc2.2
base-files
netbase
libc6
libc6-dev
make
glibc-devel
Additional you need the libaio-0.3.103-3.i386.rpm package. Convert it with
alien to an deb package and install it.
 
== LINKS ==
* [http://oracleinsider.wordpress.com/2009/04/23/installing-oracle-10g-on-linux/](http://oracleinsider.wordpress.com/2009/04/23/installing-oracle-10g-on-linux/)

---

### Post by jvictor on 2009-09-04
Awesome ! - Followed this and got oracle 10g working on Crunchbang lite ! great job.

---

