---
title: "Optimizing XLStoCSV Code in Python"
date: 2006-12-12
forum: Programming Talk
---

### Post by fsgpr on 2006-12-12
I am a relative Python/Programming noob...

Below is some code I wrote to convert XLS files to CSV.  While it works, it is rather slow on larger files.

Please let me know what the best ways to optimize this code are.  I know that I should combine strings using join, but am not quite sure how to implement it in this case... Should I join on '","', use slices to eliminate the extra characters at the beginning and end of a line, and add a '\n'?  (it just seems there should be a better way)

I am using the xlrd package from [http://www.lexicon.net/sjmachin/xlrd.htm](http://www.lexicon.net/sjmachin/xlrd.htm).

Any advice is appreciated, thanks.


```
def XLSToCSV(XLSFileName, CSVFileName):
    book = xlrd.open_workbook(XLSFileName)
    sheet = book.sheet_by_index(0)
    CSVFileString = ""
    for row in range(sheet.nrows):
        for column in range(sheet.ncols):
            if(sheet.cell_type(row, column) == xlrd.XL_CELL_DATE):
                Date = sheet.cell_value(row, column)
                Date = xlrd.xldate_as_tuple(Date, book.datemode)
                DateString = LeadingZero(Date[1]) + "/" + LeadingZero(Date[2]) + "/" + str(Date[0])           
                CSVFileString = CSVFileString + '"' + DateString + '",'
            elif(sheet.cell_type(row, column) == xlrd.XL_CELL_NUMBER):
                Number = sheet.cell_value(row, column)
                Number = str(Number)
                if(Number[-2:] == ".0"):
                    Number = Number[:-2]
                CSVFileString = CSVFileString + '"' + Number + '",'
            else:
                CSVFileString = CSVFileString + '"' + str(sheet.cell_value(row, column)) + '",'
        CSVFileString = CSVFileString + "\n"
    CSVFile = open(CSVFileName, 'w')
    CSVFile.write(CSVFileString)
    CSVFile.close()

def LeadingZero(Date):
    Date = str(Date)
    if(len(Date) == 1):
        Date = "0" + str(Date)
    return str(Date)
```

---

