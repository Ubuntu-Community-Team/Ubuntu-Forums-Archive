---
title: "Remote download manager"
date: 2007-08-31
forum: Programming Talk
---

### Post by asdasd on 2007-08-31
I'm trying to install [rdlm(link)]("http://freefoote.dview.net/linux_rdlm.html") and when I add the mysql data I get the error:

ERROR 1064 (42000) at line 3: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'USER rdlm' at line 1

Here is the rdlm.mysql file:

CREATE DATABASE rdlm;

USER rdlm;

CREATE TABLE files (
  ID int(10) unsigned NOT NULL auto_increment,
  URL text,
  parameters text,
  listname text,
  state int(10) unsigned default NULL,
  total_size int(10) unsigned default NULL,
  logfile text,
  continue int(11) default '0',
  PRIMARY KEY  (ID),
  KEY ID (ID)
) TYPE=MyISAM;

I'm using 7.04, PHP5 and latest MySQL

---

### Post by ryno519 on 2007-08-31
USE USER rdlm?

---

### Post by asdasd on 2007-08-31
thanks for the quick reply.

With that line changed I get:

ERROR 1049 (42000) at line 3: Unknown database 'USER'

and if I change it to

USE rdlm;

I get:

ERROR 1064 (42000) at line 5: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'continue int(11) default '0',
  PRIMARY KEY  (ID),
  KEY ID (ID)
) TYPE=MyISAM' at line 9

---

