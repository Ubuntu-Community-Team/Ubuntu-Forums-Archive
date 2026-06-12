---
title: "Update an Excel Spreadsheet using Database?"
date: 2007-12-17
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-12-17
I have a Java program which pulls a bunch of data out of a database.  The data somehow needs to get into and update an excel sheet.  (I currently generate a .csv file, but others want the data to be in a spreadsheet, formatted in a certain way).  I think the easiest way to do this is to have each column of the Excel sheet be a query and then have the Java program that I am using to gather the data generate some kind of a smaller database which the Excel sheet can query and update itself.  If anyone knows of a better idea, let me know.  What's the best way to update my Excel sheet with the data collected and stored in my Java program?

---

### Post by cmnorton on 2007-12-17
This is easily done from Perl. I would have to believe there is a Java Class that handles Excel spreadsheets.

---

### Post by SNYP40A1 on 2007-12-17
Does anyone know of a Java class that manipulates Excel Sheets?  I want to be able to read cells and write to cells.  Such as:

String header1 = getCell(B6);

or setCell(B6, "hello");

---

### Post by mozetti on 2007-12-17
Excel can easily read external data sources, and update the contents of the cells. If you're already using java to pull the data and make a .csv, then just set up the excel spreadsheet to pull in the data from the .csv file. Of course, depending on the setup, Excel could just pull the data straight from the database, too. Under tools (i think), there is an option to "Get External Data" and an associated toolbar for updating the spreadsheet by querying the data source.

---

### Post by ck23 on 2007-12-17
For updating Excel using Java [check out ExtenXLS.]("http://www.extentech.com/estore/product_detail.jsp?product_group_id=1")

For updating using a graphical interface, without code,[ try Exteria]("http://extentech.sheetster.com/knowledgebase/KB_weblog_detail.jsp?meme_id=1236&pg_meme_type=2").

Both use ExtenXLS 6, and have 30 day free trial versions.  [OpenXLS is the open source version]("http://www.extentech.com/estore/product_detail.jsp?product_group_id=228") and is based on ExtenXLS v4

---

### Post by SNYP40A1 on 2007-12-18
[http://www.rgagnon.com/javadetails/java-0516.html](http://www.rgagnon.com/javadetails/java-0516.html)

---

### Post by SNYP40A1 on 2007-12-20
I used JExcel and it rocks!!!

---

