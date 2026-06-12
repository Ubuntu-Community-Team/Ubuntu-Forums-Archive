---
title: "mysql error in a create table statement"
date: 2011-01-10
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-10
this wont work in mysql 5.5
it will work in mysql 5.05

if someone can look quick and see why?

> "SdlsRecord TEXT,TS TIMESTAMP(14), LOSC VARCHAR(5) DEFAULT '', LOSN DECIMAL(14,6) DEFAULT 0," & _
  "Edits char(1) DEFAULT '',TitleDuplicate VARCHAR(50) DEFAULT '',INDEX TitleduplicateIndex (TitleDuplicate(20))) ENGINE = MYISAM"
 

this is the error

 > [MySQL][ODBC 3.51 Driver][mysqld-5.5.8]You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(14), LOSC VARCHAR(5) DEFAULT '', LOSN DECIMAL(14,6) DEFAULT 0,Edits char(1) DEF' at line 1

entire table statement is this here.

>  connBlast.Execute "CREATE TABLE IF NOT EXISTS bookdata" & _
  "(Id INT AUTO_INCREMENT PRIMARY KEY," & _
  "Titles TEXT," & _
  "GeneralNote TEXT," & _
  "Author VARCHAR(100) DEFAULT '', INDEX AuthorIndex (Author(20))," & _
  "Imprint VARCHAR(100) DEFAULT ''," & _
  "ISBN VARCHAR(100) DEFAULT ''," & _
  "Description VARCHAR(100) DEFAULT ''," & _
  "CallNumberPre VARCHAR(5) DEFAULT ''," & _
  "CallNumber VARCHAR(25) DEFAULT '', INDEX CallNumberIndex (CallNumber(5))," & _
  "LOCNumber VARCHAR(100) DEFAULT ''," & _
  "Accession VARCHAR(25) DEFAULT ''," & _
  "Bibliography VARCHAR(100) DEFAULT ''," & _
  "Series VARCHAR(100) DEFAULT ''," & _
  "Mystatus VARCHAR(120) DEFAULT '', INDEX MystatusIndex (Mystatus)," & _
  "Barcode VARCHAR(50) DEFAULT '', INDEX BarcodeIndex (Barcode(10))," & _
  "LocalData VARCHAR(100) DEFAULT ''," & _
  "checkoutPeriod VARCHAR(10) DEFAULT ''," & _
  "CatalogCard TEXT," & _
  "Summary TEXT," & _
  "MyCount VARCHAR(10) DEFAULT ''," & _
  "ItemDate DATETIME," & _
  "MyUser VARCHAR(50) DEFAULT '', MarcData TEXT," & _
  "SdlsRecord TEXT,TS TIMESTAMP(14), LOSC VARCHAR(5) DEFAULT '', LOSN DECIMAL(14,6) DEFAULT 0," & _
  "Edits char(1) DEFAULT '',TitleDuplicate VARCHAR(50) DEFAULT '',INDEX TitleduplicateIndex (TitleDuplicate(20))) ENGINE = MYISAM"
  

---

### Post by sdowney717 on 2011-01-10
TS TIMESTAMP(14),

hmmm, take this one out and it works!
something must have changed with timestamp field

fixed it by just calling it TIMESTAMP

---

### Post by DaithiF on 2011-01-10
the display width suffix to the timestamp field has been ignored since mysql4.1

See [http://dev.mysql.com/doc/refman/4.1/en/timestamp.html](http://dev.mysql.com/doc/refman/4.1/en/timestamp.html) 
I guess in one of the 5.x versions they have made it an error rather than just silently ignoring it.

(leave out the (14) in case it isn't clear)

---

### Post by sdowney717 on 2011-01-10
thanks, yes that worked great (until 2037)
I dont do much with the timestamp field. I do use it comparing datetimes on some searches. I recall some suggestion some time ago on the mysql forum to add TIMESTAMP fields to tables as it helped the database keep track.
Any thoughts>?

---

