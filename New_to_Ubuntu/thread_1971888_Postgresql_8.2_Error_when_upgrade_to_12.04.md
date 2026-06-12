---
title: "Postgresql 8.2 Error when upgrade to 12.04"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by Balajoe on 2012-05-03
Dear all

This is my first time at the forum here - I tried to upgrade from 11.10 to 12.04 a couple a days but I am having a problem with updating my packages after that. The **sudo apt-get -f install** command is giving me this:-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmagick++3 amsn-data libemeraldengine0 perlmagick inkscape tcl-tls
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  postgresql-8.2
0 upgraded, 0 newly installed, 1 to remove and 660 not upgraded.
After this operation, 12.4 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 269406 files and directories currently installed.)
Removing postgresql-8.2 ...
find: `/usr/share/postgresql/8.2/tsearch_data': No such file or directory
dpkg: error processing postgresql-8.2 (--remove):
 subprocess installed pre-removal script returned error exit status 1
update-rc.d: warning: postgresql-8.2 stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (S 0 1 6)
Errors were encountered while processing:
 postgresql-8.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried to do "**sudo apt-get --purge remove postgresql-8.2**" but I am getting the same error:-

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmagick++3 amsn-data libemeraldengine0 perlmagick inkscape tcl-tls
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  postgresql-8.2*
0 upgraded, 0 newly installed, 1 to remove and 660 not upgraded.
After this operation, 12.4 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 269406 files and directories currently installed.)
Removing postgresql-8.2 ...
find: `/usr/share/postgresql/8.2/tsearch_data': No such file or directory
dpkg: error processing postgresql-8.2 (--purge):
 subprocess installed pre-removal script returned error exit status 1
update-rc.d: warning: postgresql-8.2 stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (S 0 1 6)
Errors were encountered while processing:

I ran "**dpkg -l | grep postgres**" and got this:-

pi  postgresql-8.2                                8.2.7-1                                    object-relational SQL database, version 8.2 server
pi  postgresql-client-8.2                         8.2.7-1                                    front-end programs for PostgreSQL 8.2
ii  postgresql-client-common                      129                                        manager for multiple PostgreSQL client versions

Now my update manager is not working and I can't open others like text editors. I can open Synaptic Package Manager but I cannot fix the broken package (postgresql 8.2) - the removal is giving me the same error as above. I tried to install postgresql 9.1 from the package manager but this requires me to remove 8.2 which is the problem. Message returned:-

E: postgresql-8.2: subprocess installed pre-removal script returned error exit status 1

What else I can do? Please help! Thanks

---

### Post by AriSanguinetti on 2012-05-07
This error means that the file tsearch_data is missing or corrupt. To solve it, run the following:

```
sudo touch /usr/share/postgresql/8.2/tsearch_data
```

REMEMBER that the file tsearch_data will be overwritten.

Saludos!

---

### Post by Balajoe on 2012-05-08
> **AriSanguinetti said:**
> This error means that the file tsearch_data is missing or corrupt. To solve it, run the following:

```
sudo touch /usr/share/postgresql/8.2/tsearch_data
```REMEMBER that the file tsearch_data will be overwritten.

Saludos!

Yes, that did the trick - thanks alot!

---

