---
title: "php, excel, and pdfs"
date: 2006-01-26
forum: Programming Talk
---

### Post by Silent1 on 2006-01-26
i searched the forum and found some projects that allow me to create excel or pdfs with php. I'm just wondering if it would be possible to create new pdfs or excel sheets in php when the originals were created in excel.

Here is the issue, client creates most their forms for their clients and employees in excel but wants a solution where the excel/pdf file can be recreated with all the data filled in on their website. They would also like the option that a pdf can be created based on the prefilled excel sheet. This possible? Thank in advance.

---

### Post by [2]BoxingFiend on 2006-01-26
As to excel file.  I have been using Spreadsheet_Excel_Writer module from PEAR.  It does not "create" an Excel file, but rather send it to via the http request for the end user to invoke excel to read it.  It has most features of excel, cell formating, formulas, multiple worksheets.  Right now it cannot write to a file for download.  But with relation to php+mysql => excel it's excellent.  I was able to use it to generate budget files at work of an excel file contain 76 worksheets, and about 250k cell of data and formulas.  

Although this module cannot read or write from an excel file.  It did not take me too long to add marker values in the mysql db so that the user can generate the report based upon a range.

As to pdf, there are several packages available, but I have yet to try any.  I'm gonna try some of the PEAR modules.  Will follow up once I have a chance to test them out.

---

