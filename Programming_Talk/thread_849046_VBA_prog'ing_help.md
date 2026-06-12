---
title: "VBA prog'ing help"
date: 2008-07-04
forum: Programming Talk
---

### Post by rahul.sharma on 2008-07-04
Hi 

I have a VBA programming problem. I have a data with over 200000 rows. But limitation in excel for over 
65000 rows doesn't allow to fit data in one excel sheet. So i splitted the data in 20000 rows chunks. 

But now i have one problem : I have one column, column_nbr that has value 1 to 99. 
I want when data get splitted one column value should not distributed in 2 worksheet . 

i.e., If sheet 1 has data for column_nbr 1 to 20 then for col 20 all values should be in same sheet 
and same time maintain the condition of 20000 rows in one sheet only. 

Can anybody help me for code for above problem...

---

### Post by ghostdog74 on 2008-07-04
1) you might want to try other forums for responses besides here
eg[ here]("http://groups.google.com.sg/group/microsoft.public.excel.misc?hl=en&lnk=sg") , [here]("http://groups.google.com.sg/group/microsoft.public.word.vba.general?hl=en&lnk=srg") and [here]("http://groups.google.com.sg/group/excel-macros?hl=en&lnk=srg")

2) show samples of your data file and sample of how your output will look like

---

### Post by pmasiar on 2008-07-05
You can generate XML for multi-sheet excel files, and properly adjust values. I know text processing in VBA kinda sucks, but that's you penance for using such language :-)

---

