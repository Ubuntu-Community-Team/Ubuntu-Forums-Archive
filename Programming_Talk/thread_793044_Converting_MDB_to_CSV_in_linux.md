---
title: "Converting MDB to CSV in linux?"
date: 2008-05-13
forum: Programming Talk
---

### Post by iheartubuntu on 2008-05-13
Not sure if this is the place for this, but... one of my brothers made an MSaccess database program several years ago for my dad so my dad can enter business contacts and sort them by category (tube bending, anodizing, x-ray, blueprints, etc). 

I got my dad using Ubuntu about 2 months ago and he loves it, but he needs his database of contacts. The file wont work in the various linux database programs that should read MDB files, so Im trying to somehow convert the MDB file to CSV so my dad can just dump all those contacts in his evolution mail.

This is where im stuck. I installed "mdbtools" and ran it based on instructions here: [http://blog.moybella.net/2007/03/10/converting-microsoft-access-mdb-into-csv-or-mysql-in-linux/](http://blog.moybella.net/2007/03/10/converting-microsoft-access-mdb-into-csv-or-mysql-in-linux/)

In the terminal I get all the info from the file, but it doesnt look not well organized and the first part of the info is not available. I tried copying what I could and saved it to a CSV file, but importing that into evolution gives me a bunch of junk (basically all info in the wrong places).

Is there any other programs I can use to convert MDB to CSV? Any help would be greatly appreciated! Thanks - Dave

---

### Post by omrsafetyo on 2008-05-13
Have you tried exporting your database as a flat text file (csv, dat, etc.) from access, and then importing?  You can use VBA:

```
DoCmd.TransferText acExportDelim, "", "TABLE_NAME", "C:\TEMP\contacts.csv", False, "" 
```

You can then import your data into any database management tool in Ubuntu, for instance with dbaccess for informix, you would use:

```
load from contacts.csv 
insert into myContacts

```

Or for MySQL:
```

LOAD DATA LOCAL INFILE '~/contacts.csv'
INTO TABLE myContacts
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n';

```
That will get your contacts into a database on Ubuntu... but so far as importing into evolution, try this thread:

[http://ubuntuforums.org/showthread.php?t=321879](http://ubuntuforums.org/showthread.php?t=321879)

That thread mentions that contact exports from different programs use different formats, and that importing into evolution can be mapped to the wrong fields.  You can tweak your CSV to match the mapping you're importing to.  You could do this with awk - just cat the file, pipe it to awk, and then use '{print $5, %3, $1, $2}' or etc. to print the columns in the order you want.

---

