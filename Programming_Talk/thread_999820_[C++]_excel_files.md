---
title: "[C++] excel files?"
date: 2008-12-02
forum: Programming Talk
---

### Post by StOoZ on 2008-12-02
does anyone know of a good lib (any library actually) to work with excel file (not csv...) , for C \ C++???

I cant find anything *free* for that...

---

### Post by StOoZ on 2008-12-02
no one?
:cry:

---

### Post by rbprogrammer on 2008-12-02
I don't know of any, but I know OpenOffice is able to open excel files.  Also OpenOffice is open source.  So if you really needed to get access to excel files and had the time to sift through the OpenOffice source code, you might find an answer there.

---

### Post by Zugzwang on 2008-12-03
Also, there's an easy-to-use library for Java, namely one of the Apache collection (POI?). That one is quite good (I used it once), you could try interfacing it (using one of various methods).

---

### Post by amauk on 2008-12-03
Openoffice is probably your best bet

Openoffice can be scripted on the command line (Ie. no GUI or anything)
just acting as a set of CLI programs

Haven't really used the CLI capabilities of Openoffice all that much, but I believe all features available via the GUI are there on the command line as well

there's a fair number of tutorials on the net

---

### Post by scoon on 2008-12-03
Hey there, 

I don't know if either of these ideas will work for you, but here are a couple of things I have done in the past. 

In M$ land, the excel file can be a data source for the ADO so that you can use it just like a database table. 

With MySQL, you can do the following: 
```
LOAD DATA INFILE 'data.txt' INTO TABLE tbl_name
FIELDS TERMINATED BY ',' 
LINES TERMINATED BY '\n';
```
I've done the MySQL trick with excel's converted to CSVs.

Hopefully either one of these ways can help you.

Thanks.

---

### Post by StOoZ on 2008-12-03
first of all thanks to you all.
secondly , the excel file has one column with string , and another column with string , thats it .... but ... with 500,000 lines.

I need to read & write it as an xls file , not csv , if I needed to read it as a csv I could use fstream..

about the OO solution , i'll give it a go...
but , do you think I can use SQL / MySQL queries to retrieve and insert data into xls files?

---

