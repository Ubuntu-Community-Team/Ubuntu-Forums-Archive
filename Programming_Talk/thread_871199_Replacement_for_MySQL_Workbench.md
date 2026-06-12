---
title: "Replacement for MySQL Workbench?"
date: 2008-07-26
forum: Programming Talk
---

### Post by mech7 on 2008-07-26
Is there any on linux? :(

---

### Post by scragar on 2008-07-26
you can build it for linux from source, although I have not done it myself:

[https://help.ubuntu.com/community/MySqlWorkBench](https://help.ubuntu.com/community/MySqlWorkBench)


EDIT: a google search revealed that at one point there was an svn version, I'll take a look see if I can find it.

---

### Post by mech7 on 2008-07-26
> **scragar said:**
> you can build it for linux from source, although I have not done it myself:

[https://help.ubuntu.com/community/MySqlWorkBench](https://help.ubuntu.com/community/MySqlWorkBench)


EDIT: a google search revealed that at one point there was an svn version, I'll take a look see if I can find it.

Hmmm well i built it from SVN...

But it says: 

(mysql-workbench-bin:26960): libglade-WARNING **: could not find glade file '/usr/local/usr/local/share/mysql-gui/workbench/document.glade'
terminate called after throwing an instance of 'MGGladeXML::Error'
Aborted
chris@chris-laptop:~$

Here is a solution i think?
[http://forums.mysql.com/read.php?113,131982,132183](http://forums.mysql.com/read.php?113,131982,132183)

But what do i do with this?



root@moveaway:/opt/mysql-workbench/bin# MWB_DIR=/ /opt/mysql-workbench/bin/mysql-workbench-bin  ???

---

### Post by tinny on 2008-07-26
[DBDesigner4]("http://www.fabforce.net/dbdesigner4/") is what you want!

[http://www.fabforce.net/dbdesigner4/downloads.php](http://www.fabforce.net/dbdesigner4/downloads.php)

Here is a tutorial that will help you.

[http://knightlust.blogspot.com/search?q=dbdesigner](http://knightlust.blogspot.com/search?q=dbdesigner)

FYI: MySQL Workbench is a fork of DBDesigner4.

---

### Post by mech7 on 2008-07-26
Hmmm but Db Designer runs crap on linux :( also its no longer being developed... Workbench is the new DbDesigner..

> **tinny said:**
> [DBDesigner4]("http://www.fabforce.net/dbdesigner4/") is what you want!

[http://www.fabforce.net/dbdesigner4/downloads.php](http://www.fabforce.net/dbdesigner4/downloads.php)

Here is a tutorial that will help you.

[http://knightlust.blogspot.com/search?q=dbdesigner](http://knightlust.blogspot.com/search?q=dbdesigner)

FYI: MySQL Workbench is a fork of DBDesigner4.

---

### Post by tinny on 2008-07-26
> 
Hmmm but Db Designer runs crap on linux  also its no longer being developed... Workbench is the new DbDesigner..


:confused:

Runs fine for me and others on this forum. Have you tried it?

Sure its on the way out, but it will do until a Linux version of MySQL Workbench is released (it will be). Also MySQL Workbench can open DBDesigner4 files so you can migrate them later. 

But its up to you...

---

### Post by mech7 on 2008-07-26
Yes I have tried it but could never connect... only the windows version worked for me :(

> **tinny said:**
> :confused:

Runs fine for me and others on this forum. Have you tried it?

Sure its on the way out, but it will do until a Linux version of MySQL Workbench is released (it will be). Also MySQL Workbench can open DBDesigner4 files so you can migrate them later. 

But its up to you...

---

### Post by tinny on 2008-07-26
> **mech7 said:**
> Yes I have tried it but could never connect... only the windows version worked for me :(

oh yes. That doesnt work :(

What you have to do is export your design as an sql file (export creates) and then load the create script using MySQL query browser.

---

### Post by mech7 on 2008-07-26
Ah I have it running now: 

chris@chris-laptop:/usr/local$ sudo ln -s /usr

:popcorn:

---

### Post by mothraman on 2008-12-02
I followed the instructions in the link privided by tinny  I get "sudo cp DbxMda/libsqlmda.so.4.20 /usr/li
cp: cannot stat `DbxMda/libsqlmda.so.4.20': No such file or directory"

on the third step

Any thoughts?

I'm running Intrepid.

---

### Post by tinny on 2008-12-02
The installation of MySQL Workbench on Ubuntu has become quite simple.

1. Download and then install google-ctemplate:

[http://google-ctemplate.googlecode.com/files/libctemplate0_0.92-1_i386.deb](http://google-ctemplate.googlecode.com/files/libctemplate0_0.92-1_i386.deb)

2. Install dependencies

```

sudo apt-get install liblua5.1-0

```

```

sudo apt-get install libzip1

```


3. Download and install MySQL Workbench


[ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/mysql-workbench_5.1.4-1_i386.deb](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/mysql-workbench_5.1.4-1_i386.deb)

DONE!!! :-)

This is an Alpha version but seems to be stable.

---

### Post by scragar on 2008-12-02
> **tinny said:**
> The installation of MySQL Workbench on Ubuntu has become quite simple.

1. Download and then install google-ctemplate:

[http://google-ctemplate.googlecode.com/files/libctemplate0_0.92-1_i386.deb](http://google-ctemplate.googlecode.com/files/libctemplate0_0.92-1_i386.deb)

2. Install dependencies

```

sudo apt-get install liblua5.1-0

```

```

sudo apt-get install libzip1

```


3. Download and install MySQL Workbench


[ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/mysql-workbench_5.1.4-1_i386.deb](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/mysql-workbench_5.1.4-1_i386.deb)

DONE!!! :-)

This is an Alpha version but seems to be stable.

You do know that dependencies are automaticly installed on .debs unless you force it(which is always a bad idea).

oh, and the two middle steps can be merged:
```
sudo apt-get install liblua5.1-0 libzip1
```

---

### Post by tinny on 2008-12-02
> **scragar said:**
> You do know that dependencies are automaticly installed on .debs unless you force it(which is always a bad idea).

oh, and the two middle steps can be merged:
```
sudo apt-get install liblua5.1-0 libzip1
```

Yeah I did know that .....so???

Did my example not work?

---

### Post by mothraman on 2008-12-02
Thanks Tinny and Scragar,

You're right---it installs nicely (or says it does).  However, when I try to run  it I get:
usr@compter:/usr/bin$ mysql-workbench
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/forms.grt.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/wb.model.grt.so' (cpp)
** Message: WARNING: Could not open module /usr/lib/mysql-workbench/modules/wb.model.grt.so (/usr/lib/mysql-workbench/modules/wb.model.grt.so: undefined symbol: _ZNK6google8Template14ExpandWithDataEPSsPKNS_18TemplateDictionaryEPKNS_9ctemplate13PerExpandDataE)    
** Message: WARNING: Could not load wb.model.grt.so: Cannot open /usr/lib/mysql-workbench/modules/wb.model.grt.so    
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/db.mysql.grt.so' (cpp)
** Message: WARNING: Could not open module /usr/lib/mysql-workbench/modules/db.mysql.grt.so (/usr/lib/mysql-workbench/modules/db.mysql.grt.so: undefined symbol: _ZNK6google8Template14ExpandWithDataEPSsPKNS_18TemplateDictionaryEPKNS_9ctemplate13PerExpandDataE)    
** Message: WARNING: Could not load db.mysql.grt.so: Cannot open /usr/lib/mysql-workbench/modules/db.mysql.grt.so    
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/db.mysql.sqlparser.grt.so' (cpp)

** (mysql-workbench-bin:12953): WARNING **: Native C++ module classes must have the suffix Impl to avoid confusion between implementation and wrapper classes (MysqlSqlFacade)
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/wb.mysql.import.grt.so' (cpp)
** Message: WARNING: Could not open module /usr/lib/mysql-workbench/modules/wb.mysql.import.grt.so (/usr/lib/mysql-workbench/modules/wb.mysql.import.grt.so: undefined symbol: _ZN19Mysql_sql_parser_feC1Ev)    
** Message: WARNING: Could not load wb.mysql.import.grt.so: Cannot open /usr/lib/mysql-workbench/modules/wb.mysql.import.grt.so    
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/dbutils.grt.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/plugins/db.mysql.wbp.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/plugins/db.wbp.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/plugins/db.mysql.editors.wbp.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/plugins/wb.model.editors.wbp.so' (cpp)

(mysql-workbench-bin:12953): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
** Message: item_activated: 0x9d45c38 -> 'builtin:web_home'
** Message: item_activated: 0x9d277c8 -> 'builtin:wb.doc_properties'
lem@Lampie:/usr/bin$ mysql-workbench
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/forms.grt.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/wb.model.grt.so' (cpp)
** Message: WARNING: Could not open module /usr/lib/mysql-workbench/modules/wb.model.grt.so (/usr/lib/mysql-workbench/modules/wb.model.grt.so: undefined symbol: _ZNK6google8Template14ExpandWithDataEPSsPKNS_18TemplateDictionaryEPKNS_9ctemplate13PerExpandDataE)    
** Message: WARNING: Could not load wb.model.grt.so: Cannot open /usr/lib/mysql-workbench/modules/wb.model.grt.so    
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/db.mysql.grt.so' (cpp)
** Message: WARNING: Could not open module /usr/lib/mysql-workbench/modules/db.mysql.grt.so (/usr/lib/mysql-workbench/modules/db.mysql.grt.so: undefined symbol: _ZNK6google8Template14ExpandWithDataEPSsPKNS_18TemplateDictionaryEPKNS_9ctemplate13PerExpandDataE)    
** Message: WARNING: Could not load db.mysql.grt.so: Cannot open /usr/lib/mysql-workbench/modules/db.mysql.grt.so    
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/db.mysql.sqlparser.grt.so' (cpp)

** (mysql-workbench-bin:13002): WARNING **: Native C++ module classes must have the suffix Impl to avoid confusion between implementation and wrapper classes (MysqlSqlFacade)
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/wb.mysql.import.grt.so' (cpp)
** Message: WARNING: Could not open module /usr/lib/mysql-workbench/modules/wb.mysql.import.grt.so (/usr/lib/mysql-workbench/modules/wb.mysql.import.grt.so: undefined symbol: _ZN19Mysql_sql_parser_feC1Ev)    
** Message: WARNING: Could not load wb.mysql.import.grt.so: Cannot open /usr/lib/mysql-workbench/modules/wb.mysql.import.grt.so    
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/dbutils.grt.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/plugins/db.mysql.wbp.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/plugins/db.wbp.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/plugins/db.mysql.editors.wbp.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/plugins/wb.model.editors.wbp.so' (cpp)

(mysql-workbench-bin:13002): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
** Message: item_activated: 0x9e4bdb0 -> 'builtin:web_mysql_home'
** Message: item_activated: 0x9e46a38 -> 'builtin:web_home'

What did I miss?

---

### Post by scragar on 2008-12-02
i just thought when giving instructions it would have been better to skip the steps that didn't need to be done.

---

### Post by tinny on 2008-12-02
> **mothraman said:**
> Thanks Tinny and Scragar,

You're right---it installs nicely (or says it does).  However, when I try to run  it I get:
usr@compter:/usr/bin$ mysql-workbench
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/forms.grt.so' (cpp)
** Message: Trying to load module '/usr/lib/mysql-workbench/modules/wb.model.grt.so' (cpp)


I get all of those messages too when I run the application from the command line.

Usually I just fun it from the Applications Menu in Gnome and it all seems to run fine. I guess what you are seeing is just internal application logging.

I would suggest you have a play with it and see how stable it feels for you.

---

### Post by mothraman on 2008-12-03
> **tinny said:**
> I get all of those messages too when I run the application from the command line.

Usually I just fun it from the Applications Menu in Gnome and it all seems to run fine. I guess what you are seeing is just internal application logging.

I would suggest you have a play with it and see how stable it feels for you.

OK.  I'll work with it.  After a quick look, I can't get it to do much. Most menu options are greyed out.  I don't see where to connect to an existing database to work with it. It crashes when I click on the add table icon.  The only documentation I can find is for the windows version. I'll have to take a look at that.

Thanks for your help.

---

### Post by tinny on 2008-12-03
> **mothraman said:**
> OK.  I'll work with it.  After a quick look, I can't get it to do much. Most menu options are greyed out.  I don't see where to connect to an existing database to work with it. 


Some features like the direct DB connection functionality are for the enterprise version only (paid version). In the free version you can export your diagram as an SQL create script and then run that script against your DB.

> **mothraman said:**
> 
It crashes when I click on the add table icon.  The only documentation I can find is for the windows version. I'll have to take a look at that.

Thanks for your help.

I guess thats alpha software....

Strange that you are having these fundamental problems. It has been working fine for me.

---

### Post by schkovich on 2009-08-05
Debian package of MySql Workbench 5.1 is available for download. Several restrictions have been removed from community edition.

[FAQ]("http://dev.mysql.com/workbench/?page_id=29")
[Compare]("http://dev.mysql.com/workbench/?page_id=11")
[Download]("http://dev.mysql.com/downloads/workbench/5.1.html")
[Do It Yourself]("http://dev.mysql.com/workbench/?page_id=152")

I've installed Ubuntu 8.10 amd64 (DEB) package on Ubuntu 9.04 without a problem and it works like charm.

---

### Post by another_sam on 2009-11-02
just updated
[https://help.ubuntu.com/community/MySqlWorkBench](https://help.ubuntu.com/community/MySqlWorkBench)
with what worked for me on Ubuntu 9.10

launching the .deb directly did not created the entry on the menu. I guess it could be because of the difference between versions (.deb for 9.04, vs system 9.10)

---

### Post by CostaRica on 2009-11-03
I just installed it in my Ubuntu 9.10 virtualbox and works just fine.  It also included it in the programming menu.

---

### Post by lokisapocalypse on 2010-06-26
I attempted to follow the instructions in this thread and at [https://help.ubuntu.com/community/MySqlWorkBench](https://help.ubuntu.com/community/MySqlWorkBench) but when I run

```
sudo apt-get install libmysqlclient15off
```

I get the following message:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmysqlclient15off is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmysqlclient15off has no installation candidate


With that, the install of mysql workbench fails because of that dependency. Is there a workaround for it?

---

### Post by lokisapocalypse on 2010-06-26
Why yes there is: [http://packages.ubuntu.com/karmic/i386/libmysqlclient15off/download](http://packages.ubuntu.com/karmic/i386/libmysqlclient15off/download)

---

### Post by Flaggmann on 2011-07-02
MySQL Navigator

phpmyadmin

phppgadmin

MySQLworkbench is the latest morphing away from MySQL Administrator/ MySQL Query Browser pair.

---

