---
title: "Copy data upto last used Row of a specific column"
date: 2013-02-16
forum: Programming Talk
---

### Post by Praveen30 on 2013-02-16
There are some excel files in a folder.I need to copy a specific column from all the excel files and paste it into a single excel file.I want to copy upto last used rows column values.I know how to get last used row number but how to use it to get the copy range of column upto that row no.

I am using this code to get the last used rows-

**rowNo=objExcel.Activeworkbook.Sheets(1).UsedRange.Rows.count**

Now, i want to copy the data of a specific column upto last row used.

//What to write in the below code to use rowNo //

**Set Source=objExcel.Activeworkbook.Sheets(1).Column("G")**

[B]Source.Copy
[/B]
Language- VBScript

---

### Post by muteXe on 2013-02-17
Ain't done excel stuff in years, but is it possible to get back the contents of one column as an array?

---

