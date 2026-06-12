---
title: "[Python] Creating Spreadsheets"
date: 2008-08-13
forum: Programming Talk
---

### Post by TreeFinger on 2008-08-13
Is there a way to create and add data to spreadsheets through python?

Only thing I have found is this: [http://sourceforge.net/projects/pyexcelerator/?abmode=1](http://sourceforge.net/projects/pyexcelerator/?abmode=1)

---

### Post by Zugzwang on 2008-08-13
Do you really need formatting the data? If not, use .csv instead.

Apart from that, there's an excellent Java library for that (Apache POI). You might be able to use that from within Python somehow.

---

### Post by Reiger on 2008-08-13
I would recommend the csv format.

---

### Post by stevescripts on 2008-08-13
+1 more for using csv

---

### Post by TreeFinger on 2008-08-13
pyExcelerator seems to be working fine and if I used cvs the end user would have to enter the separation character (delimiter?). So this seems better.

---

### Post by Reiger on 2008-08-13
AFAIK Not if you used the default format (one csv isn't neccesarily the same as the other ;)); using double quotes ("") wrapped around your 'cell values'...

---

