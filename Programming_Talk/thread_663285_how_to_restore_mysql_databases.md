---
title: "how to restore mysql databases?"
date: 2008-01-10
forum: Programming Talk
---

### Post by figo2476 on 2008-01-10
I know it is not really related to ubuntu, but I cannot find answers after many posts. Then I think I may try it here.

* I duplicated everything inside the mysql/
* I reinstalled mysql 5.0.45 in mac tiger
* I copy a backup database into mysql/data/, hoping to restore it.
* phpmyadmin can count 5 tables, but only 1 table is selectable -- click to see the data. The others are not visible.

* inside mysql/data/sample_db
drwxr-xr-x 10 mysql mysql 340 Jan 10 12:51 .
drwxr-xr-x 11 mysql mysql 374 Jan 10 15:01 ..
-rw-r----- 1 mysql mysql 65 Jan 10 12:51 db.opt
-rw-r----- 1 mysql mysql 8698 Jan 10 12:51 map.frm
-rw-r----- 1 mysql mysql 8824 Jan 10 12:51 map_item.frm
-rw-r----- 1 mysql mysql 4864 Jan 10 12:51 news.MYD
-rw-r----- 1 mysql mysql 2048 Jan 10 12:51 news.MYI
-rw-r----- 1 mysql mysql 8770 Jan 10 12:51 news.frm
-rw-r----- 1 mysql mysql 8820 Jan 10 12:51 page.frm
-rw-r----- 1 mysql mysql 8742 Jan 10 12:51 user.frm

news is selectable, the others are not. They are not visible in phpmyadmin

* Access denied for user 'mysql'@'localhost' (using password: NO), when just typing  shell>mysql5 -- it means user 'mysql' is not table

* I try to repair table, so I do:
change db;
repair table map;
then it says cannot find sample_db.map
(isn't map.frm there?)

---

### Post by iiibill on 2008-01-10
I am assuming you are talking about myisam tables.  You should bring up a terminal window and run myisamchk. It is simplest to go to the directory were the table files are and us a command line like:

myisamchk -o table_name

The utility has lots of documentation if you just run it with no parameters.

Note, the best way to do this is not copying the binary files, but extracting the data using mysqldump.  This creates a text file with insert statements.  Then you can just reload the data using the mysql client.

Bill

---

### Post by iiibill on 2008-01-10
Oh, I should have look closer at your directory listing.  You are missing files and without them you are not going to get anything back.

-rw-r----- 1 mysql mysql 65 Jan 10 12:51 db.opt
-rw-r----- 1 mysql mysql 8698 Jan 10 12:51 map.frm
-rw-r----- 1 mysql mysql 8824 Jan 10 12:51 map_item.frm
-rw-r----- 1 mysql mysql 4864 Jan 10 12:51 news.MYD
-rw-r----- 1 mysql mysql 2048 Jan 10 12:51 news.MYI
-rw-r----- 1 mysql mysql 8770 Jan 10 12:51 news.frm
-rw-r----- 1 mysql mysql 8820 Jan 10 12:51 page.frm
-rw-r----- 1 mysql mysql 8742 Jan 10 12:51 user.frm

A table must have a frm, MYD and MYI file.  That is meta-data, data, and index files respectively.  If you don't have those somewhere for user, page, map, and map_item tables you are out of luck.

Bill

---

### Post by figo2476 on 2008-01-10
some files natively don't have those MYD, MYI files...
so ...?

---

### Post by figo2476 on 2008-01-10
I looked into other applications' databases. Not all of them have these 2 types of files.....

---

### Post by iiibill on 2008-01-10
> **figo2476 said:**
> I looked into other applications' databases. Not all of them have these 2 types of files.....

Not sure what makes you think that.  You actually have confirmed that this is not the case because you are missing tables when you use your mysql client application, whatever that is.  You know you should really spend some time at [http://www.mysql.com](http://www.mysql.com).  Here is a relevant excerpt:

"Each MyISAM table is stored on disk in three files. The files have names that begin with the table name and have an extension to indicate the file type. An .frm  file stores the table format. The data file has an .MYD (MYData) extension. The index file has an .MYI  (MYIndex) extension."

Bill

---

### Post by steve2727 on 2008-04-03
It may be that the tables that just have *.frm files are actually InnoDB type tables rather than MyISAM tables. These can run side by side in the same MySQL database.

Instead of having 3 files stored in the database's folder under MySQL Installation Folder/data, they just have an frm file in there and the data is stored in ibdata files found directly in MySQL Installation folder/data

I found that copying the ibdata files along with my database folders restored my InnoDB tables.

Stephen Hand

Handy Solutions Ltd.

[http://www.handy-solutions.com](http://www.handy-solutions.com)

---

