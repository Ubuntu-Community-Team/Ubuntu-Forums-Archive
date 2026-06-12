---
title: "Can't Uninstall or Re-Install gammu-smsd"
date: 2020-10-30
forum: New to Ubuntu
---

### Post by martinjdz on 2020-10-30
Running Ubuntu 20.04 (LTS) with the MATE desktop environment on a desktop PC. I have a dual-boot configuration (Linux and Win10).

I recently tried to install the gammu SMS text messaging application using Synaptic Package Manager. I also selected the gammu-smsd daemon for installation.

Unfortunately, there is some kind of corruption in the gammu-smsd application file (or files). As a result, Ubuntu could not complete the installation. Now, I am "stuck." I cannot remove gammu-smsd, nor can I re-install it. Both attempts get me an error message such as:
```
 error processing package gammu-smsd:
package is in a very bad inconsistent state; you should
reinstall it before attempting configuration
```

Suddenly, I am also no longer able to access files on my Sansa Fuze MP3 player, which is an MTP device. Ubuntu recognizes the memory card inside the player, but it can no longer access the core memory inside of the player. (I can still access USB-attached flash drives and Android tablets, however.)

Additionally, I can no longer install any other utility that might help with MTP devices or USB devices, such as mtp-detect. I get the same type of error message shown above. In fact, just about any new software update causes the above error message to be displayed. Clearly, I must remove gammu-smsd somehow.

I really don't want to have to re-install the OS to fix this problem. Is there some other solution?


Here are the files that were installed for gammu-smsd:
Would manually deleting some or all of these files get rid of it, or would that make things even worse?

```
[FONT=courier new]/etc
/etc/default
/etc/default/gammu-smsd
/etc/gammu-smsdrc
/etc/init.d
/etc/init.d/gammu-smsd
/lib
/lib/systemd
/lib/systemd/system
/lib/systemd/system/gammu-smsd.service
/usr
/usr/bin
/usr/bin/gammu-smsd
/usr/bin/gammu-smsd-inject
/usr/bin/gammu-smsd-monitor
/usr/share
/usr/share/doc
/usr/share/doc/gammu-smsd
/usr/share/doc/gammu-smsd/changelog.Debian.gz
/usr/share/doc/gammu-smsd/copyright
/usr/share/doc/gammu-smsd/examples
/usr/share/doc/gammu-smsd/examples/mysql-legacy.sql.gz
/usr/share/doc/gammu-smsd/examples/mysql.sql.gz
/usr/share/doc/gammu-smsd/examples/pgsql.sql.gz
/usr/share/doc/gammu-smsd/examples/sqlite.sql.gz
/usr/share/man 
/usr/share/man/man1
/usr/share/man/man1/gammu-smsd-inject.1.gz
/usr/share/man/man1/gammu-smsd-monitor.1.gz
/usr/share/man/man1/gammu-smsd.1.gz
/usr/share/man/man5
/usr/share/man/man5/gammu-smsdrc.5.gz
/usr/share/man/man7
/usr/share/man/man7/gammu-smsd-dbi.7.gz
/usr/share/man/man7/gammu-smsd-files.7.gz
/usr/share/man/man7/gammu-smsd-mysql.7.gz
/usr/share/man/man7/gammu-smsd-null.7.gz
/usr/share/man/man7/gammu-smsd-odbc.7.gz
/usr/share/man/man7/gammu-smsd-pgsql.7.gz
/usr/share/man/man7/gammu-smsd-run.7.gz
/usr/share/man/man7/gammu-smsd-sql.7.gz
/usr/share/man/man7/gammu-smsd-tables.7.gz
/var
/var/spool
/var/spool/gammu
/var/spool/gammu/error
/var/spool/gammu/inbox
/var/spool/gammu/outbox
/var/spool/gammu/sent[/FONT]
```

[FONT=arial][SIZE=4]**I Must Re-Install the OS**[/SIZE][/FONT]
Sorry, but after less than one day, my system is becomming more and more unstable. The desktop keeps crashing, and I'm afraid that I must re-install the OS. Please remove this thread, unless someone would like to make comments about the problem.

---

### Post by wildmanne39 on 2020-10-30
Hello and welcome to the forum.

*Thread moved to **New to Ubuntu for a more appropriate fit**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

