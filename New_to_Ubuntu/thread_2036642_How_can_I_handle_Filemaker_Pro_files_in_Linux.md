---
title: "How can I handle Filemaker Pro files in Linux?"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by JohnTho on 2012-08-02
This is a new thread on this topic at the request of a Mod.

I've just started using Ubuntu (12.04) and I'm looking for a way to  migrate some Filemaker Pro files to an open-source database. I've  installed LibreOffice Base but I now either need to find a common file format  that Filemaker can export and Base can import or an application that can open and/or convert the Filemaker files.

As I'm a lazy sod at the best of times I'd really prefer a solution that avoids me having to re-create the layouts from scratch. As far as I can  see the formats exported by my version of Filemaker are:

.tab : tab-separated text
.csv : comma-separated text

I know these only contain the data. The following ones I have no knowledge of:

.slk : SYLK
.dbf : DBF
.wk1 : Lotus 1-2-3
.bas : Basic (is that as in the BASIC programming language?)
.mer : Merge
.htm : HTML table files

Can any of these formats be opened/imported by Base? If not can anyone  suggest another open-source database application or conversion utility that can handle any of  them, or better still open the native .fp5 files?

---

### Post by oldfred on 2012-08-02
Can you export to .dbf. That is the old dBase file structure which is very well known and has the column info at the beginning of the file.

But any conversion is always an issue. Some data types never map to the new data type. Some times text has invalid characters or extra quotes in names that confuse conversion software.  And the more types of databases you use the more difficult it will be.

---

### Post by JohnTho on 2012-08-02
Yes, my version of Filemaker can export to all the formats listed in my original post. I'll give .dbf a try then. Fingers crossed.....:)

---

