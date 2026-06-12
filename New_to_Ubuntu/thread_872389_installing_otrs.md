---
title: "installing otrs"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by ilplinux_tester on 2008-07-27
hello i try to install otrs(open source trouble ticketing system) but have an error and not not sucessfully install. i try to retry and retry(skipped all questions) but still the same. please help me to solve this :(

---

### Post by Partyboi2 on 2008-07-28
How are you trying to install it? What is the error message you are getting?
[B]
[/B]

---

### Post by ilplinux_tester on 2008-07-28
this error repeated everytime i try to install



> root@intern-desktop:~# apt-get install otrs2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libnet-ldap-perl otrs2-doc-en otrs2-doc-de
Recommended packages:
  libapache2-mod-perl2 libgd-graph-perl libgd-text-perl
The following NEW packages will be installed:
  otrs2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1802kB of archives.
After this operation, 12.0MB of additional disk space will be used.
Preconfiguring packages ...
/tmp/otrs2.config.174311: 50: /usr/share/otrs/bin/otrs.getConfig: not found
/tmp/otrs2.config.174311: 50: /usr/share/otrs/bin/otrs.getConfig: not found
/tmp/otrs2.config.174311: 50: /usr/share/otrs/bin/otrs.getConfig: not found
Selecting previously deselected package otrs2.
(Reading database ... 156518 files and directories currently installed.)
Unpacking otrs2 (from .../archives/otrs2_2.2.4-1_all.deb) ...
Warning: The home dir /usr/share/otrs you specified can't be accessed: No such file or directory
The user `otrs' already exists. Exiting.
Setting up otrs2 (2.2.4-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf
Replacing config file /etc/otrs/database.pm with new version
granting access to database otrs2 for otrs@localhost: success.
verifying access for otrs@localhost: success.
creating database otrs2: success.
verifying database otrs2 exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password
This module does not exist!
dpkg: error processing otrs2 (--configure):
 subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@intern-desktop:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up otrs2 (2.2.4-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf
Replacing config file /etc/otrs/database.pm with new version
granting access to database otrs2 for otrs@localhost: already exists.
creating database otrs2: already exists.
populating database via sql...  error encountered populating database:
mysql said: ERROR 1050 (42S01) at line 7: Table 'valid' already exists
dbconfig-common: otrs2 configure: aborted.
dbconfig-common: flushing administrative password
dpkg: error processing otrs2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)




>  An error seems to have occurred while installing the database. If it's of any help, this was the error encountered:                    &#9474; 
 &#9474;                                                                                                                                        &#9474; 
 &#9474; mysql said: ERROR 1050 (42S01) at line 7: Table 'valid' already exists                                                                 &#9474; 
 &#9474;                                                                                                                                        &#9474; 
 &#9474; At this point, you have the option to retry or abort the operation. If you choose "retry", you will be prompted with all the           &#9474; 
 &#9474; configuration questions once more and another attempt will be made at performing the operation. "retry (skip questions)" will          &#9474; 
 &#9474; immediately attempt the operation again, skipping all questions.  If you choose "abort", the operation will fail and you will need to  &#9474; 
 &#9474; downgrade, reinstall, reconfigure this package, or otherwise manually intervene to continue using it.  If you choose "ignore", the     &#9474; 
 &#9474; operation will continue, ignoring further errors from dbconfig-common.                                                                 &#9474; 
 &#9474;                                                                                                                                        &#9474; 
 &#9474; Error installing database for otrs2.  Retry?                                                                                           &#9474; 
 &#9474;                                                                                                                                        &#9474; 
 &#9474;                                                         abort                                                                          &#9474; 
 &#9474;                                                         retry                                                                          &#9474; 
 &#9474;                                                         retry (skip questions)                                                         &#9474; 
 &#9474;                                                         ignore                                                                         &#9474; 
 &#9474;                                                                                                                                        &#9474; 
 &#9474;                                                                                                                                        &#9474; 
 &#9474;                                                                 <Ok>                 

---

### Post by cariboo on 2008-07-28
It looks like you have to delete the databases created during the installation. log into mysql like this:

```
mysql -u root -p
```

use the password you created for root when you installed mysql, then in the mysql console type:

```
drop database otrs2;
```

This will delete the ots2 database, exit mysql:

```
\q
```

I would suggest installing the recommended packages and then try to reinstall your program again.

Jim

---

### Post by n0manarmy on 2008-10-08
I found the answer to my problem, which looks to be your problem as well here


[https://bugs.launchpad.net/ubuntu/+source/otrs2/+bug/226444](https://bugs.launchpad.net/ubuntu/+source/otrs2/+bug/226444)


[B][I]Try 'sudo apt-get install libapache2-mod-perl2-dev' before 'sudo apt-get install otrs2'

So the installation process works fine...[/I][/B]

---

### Post by anwoke8204 on 2009-02-17
I am also having issues installing otrs2, I get the following errors:

```

root@srv1:~# apt-get install otrs2
Reading package lists... Done
Building dependency tree
Reading state information... Done
otrs2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up otrs2 (2.2.4-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf
Replacing config file /etc/otrs/database.pm with new version
This module does not exist!
dpkg: error processing otrs2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any ideas on how to resolve this would be great

---

### Post by biofishfreak on 2010-01-11
try **sudo apt-get install ****libapache2-mod-perl2**

---

### Post by SgtDawg on 2010-04-13
This worked for me
```
sudo apt-get install libapache2-mod-perl2-dev
sudo apt-get purge otrs2
sudo apt-get install otrs2
```

---

