---
title: "Import data from open office spreadsheet format into gridview (GAMBAS)"
date: 2009-10-22
forum: Programming Talk
---

### Post by fairol88 on 2009-10-22
Hey guys,

I'm currently developing a program which gathers data from a spreadsheet (for example open office spreadsheet) and display it in the gridview that's provided in Gambas. 

From what I understand, let's say I want a text in row 1 and column 1.

gridview1[1,1] = "TEXT"  
However these are manual inputs and therefore fixed. Let's say my spreadsheet data in open office have the text Hello in A1. 

I'm assuming I must load the spreadsheet file first but I'm not sure what command is needed. is this possible?

data = file.load("filename") 

This probably puts the data in the filename into the variable data.

How can I extract that data into gridview?

---

### Post by Zugzwang on 2009-10-22
Unfortunately, you will have a hard time doing that. Spreadsheet programs are highly complex and it is hard to map its functionality into custom-made software. You will see that the grid view does not have a "loading" function for openoffice files. For example, the formatting capabilities for spread sheets are far bigger than those of your gridview.

Here are my 2 cents: Consider writing your spread-sheet files as .csv files. They are relatively easy to parse. You "just" have to write your own reading code of the following scheme (not actual code):
```

open "yourfile.csv" as #1
linenum = 1
do
  read #1, line
  parts = line.split(",")
  for i = 1 to length(parts)
    cells[linenum][i] = parts[i]
  end for
  linenum = linenum + 1
while line!=""
close #1

```

---

### Post by kalaharix on 2009-10-22
Hi,

I agree with Zugzwang.

However, Open Office spreadsheets are just compressed XML. If you are really dedicated you could shell from Gambas to uncompress the ods and then use the excellent string manipulation in Gambas to decifer the cell values in the xml file.

It's tricky but can be done. If you are a glass half-full sort of a guy, it is much easier to do than with an xls spreadsheet :)

I suspect Python might make a better job of importing ods. Anybody know?

The other option is to use the scripting within Open Office.

---

### Post by fairol88 on 2009-10-22
> **Zugzwang said:**
> Unfortunately, you will have a hard time doing that. Spreadsheet programs are highly complex and it is hard to map its functionality into custom-made software. You will see that the grid view does not have a "loading" function for openoffice files. For example, the formatting capabilities for spread sheets are far bigger than those of your gridview.

Here are my 2 cents: Consider writing your spread-sheet files as .csv files. They are relatively easy to parse. You "just" have to write your own reading code of the following scheme (not actual code):
```

open "yourfile.csv" as #1
linenum = 1
do
  read #1, line
  parts = line.split(",")
  for i = 1 to length(parts)
    cells[linenum][i] = parts[i]
  end for
  linenum = linenum + 1
while line!=""
close #1

```

Ahhh, I see the idea. It's pretty much allowing the data in the .csv to be read as a string and using split function to arrange words into an array depending on the seperator. 

That means I believe its best to create a function that loads a .csv file into a string, split it up and outputs an array. Is this right? If so, I should focus on that before adding the array into gridview.

Will try and keep it posted.

---

