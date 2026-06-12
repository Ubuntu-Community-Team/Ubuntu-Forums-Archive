---
title: "Utilizing Existing Data In Excel"
date: 2011-02-02
forum: Programming Talk
---

### Post by oomar on 2011-02-02
OK, so lets say you have this script in folder A. You also place
a .xls document in folder A named B.xls.

The first part of my script asks which file you want to analyze. That
works fine.

The next part is supposed to go down column "A" in the fashion of

```
a=0
b=0
xlsname = raw_input("What is the name of the spreadsheet (with
extension)? >>> ")
book = open_workbook(xlsname)
sheet = book.sheet_by_index(0)
cell = sheet.cell(a,b)
if cell.value == "":
     (exit program?)
else:
     print cell.value

```

All of the data will go in column "A" or column 0 and I just want it
to use this data until it comes upon a blank cell, which then exits
the script.

Read cell(0,0) to check if its empty, if true, exit. If false, print
cell.value(0,0)

Read cell(1,0) to check if its empty, if true, exit. If false, print
cell.value(1,0)

etc and so on. Once I get it to do this, I will have it use the data
read from the cells in a special way but it doesnt have anything to do
with excel. btw im using xlrd and xlwt

please help me if you can,

thanks,

Logan

---

### Post by oomar on 2011-02-03
Update/Bump

Here is the code I'm using now:
```
from tempfile import TemporaryFile
from xlwt import Workbook
from xlrd import open_workbook, XL_CELL_TEXT
global xlsname
xlsname = raw_input("What is the name of the spreadsheet (with extension)? >>> ")
global book
book = open_workbook(xlsname)
global sheet
sheet = book.sheet_by_index(0)
global a
a=0
global b
b=0

while 1==1:
	global cell
	cell = sheet.cell(a,b)
	if cell.value=="":
		break
	else:
		print cell.value
		global a		
		a = a + 1
```


I got this error:

```
jaypro.py:29: SyntaxWarning: name 'a' is assigned to before global declaration
  global a
```

then this error:
```
Traceback (most recent call last):
  File "jaypro.py", line 24, in <module>
    cell = sheet.cell(a,b)
  File "/usr/local/lib/python2.6/dist-packages/xlrd/sheet.py", line 255, in cell
    self._cell_types[rowx][colx],
IndexError: list index out of range

```

but it still listed out all of the cell values that I wanted it to (all of the existing column A values). So I think that's good. How should I check for the empty cells? any way to resolve the first error?

---

### Post by Zugzwang on 2011-02-03
Here's the first page that google listed for me with suitable keywords: [http://scienceoss.com/read-excel-files-from-python/](http://scienceoss.com/read-excel-files-from-python/)

You can see in the examples there that the worksheet has an attribute "nrows", which you can access to find out the number of rows in the sheet. Then, by adapting the termination condition for your loop, the problem can be solved.

By the way, the error message you pasted is certainly not one for the program you pasted, as it refers to line 29. Your program isn't that long however.

---

### Post by oomar on 2011-02-03
> **Zugzwang said:**
> Here's the first page that google listed for me with suitable keywords: [http://scienceoss.com/read-excel-files-from-python/](http://scienceoss.com/read-excel-files-from-python/)

You can see in the examples there that the worksheet has an attribute "nrows", which you can access to find out the number of rows in the sheet. Then, by adapting the termination condition for your loop, the problem can be solved.

By the way, the error message you pasted is certainly not one for the program you pasted, as it refers to line 29. Your program isn't that long however.

well i didnt paste the comments/instructions for the person im writing it for so it DOES have 29 lines. sorry about that. also I just fixed the error about the global a problem. that was easy... lol but yea that should work. Thanks! I'll post again if I need help.

---

