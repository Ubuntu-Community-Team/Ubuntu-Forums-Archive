---
title: "How to show all dates for day of the week?"
date: 2009-04-23
forum: Programming Talk
---

### Post by Chokkan on 2009-04-23
I'd like to know what the best way to get all the dates for a specific day of the week.

I'm trying to make a list of days I teach certain classes at school. Fore example I teach 1A on Wednesdays and Thursdays, and I'd like to get all the dates of every Wednesday and Thursday.

Ultimately, I'd like to print a term planner but just having a simple way to get the dates would be a start.

Is there a simple way to do this? Thanks in advance!!

---

### Post by simeon87 on 2009-04-23
I'd first determine a wednesday and then repeatedly add 7 days for as long as you still need dates. Same for other days of the week.

---

### Post by Chokkan on 2009-04-23
Yeah, I had the same vague idea of iterating over days, but I'm not sure how to integrate any of the date functions in (for example) Python to do it. I also need to combine the days as each class has 2 lessons a week.

---

### Post by Bucky Ball on 2009-04-23
I used Evolution calendar for uni all last year and it worked great. Now I use a regular diary though.

---

### Post by Marco A on 2009-04-23
.

---

### Post by croto on 2009-04-23
How about using Python's datetime library?
```

#!/usr/bin/env python

import datetime

def get_weekday_dates(start, end, weekday):
    delta = datetime.timedelta(1)
    dates = []
    while start<end:
        if start.weekday() == weekday: dates.append(start)
        start += delta
    return dates


start = datetime.date(2005,1,1)
end = datetime.date.today()

for date in get_weekday_dates(start, end, 2):
    print date.strftime("%A %B %d %Y")

```

I'm sure this can be written in a more pythonic way... I'm just learning.

---

### Post by croto on 2009-04-23
a little better:
```

#!/usr/bin/env python

import datetime

def get_weekday_dates(start, end, weekdays):
    delta = datetime.timedelta(1)
    dates = []
    while start<end:
        if start.weekday() in weekdays: dates.append(start)
        start += delta
    return dates


start = datetime.date(2005,1,1)
end = datetime.date.today()

mon_and_weds = get_weekday_dates(start, end, [0,2]);

for date in mon_and_weds:
    print date.strftime("%A %B %d %Y")

```

---

### Post by stylishpants on 2009-04-23
Fun.  

Also a fairly straightforward ruby one-liner.

```
ruby -rdate -e 'Date.today.upto(Date.parse("Jan 2010")) { |d| puts d.strftime("%10A %10B %d %Y") if [1,3].include? d.wday; }'
```

---

### Post by ghostdog74 on 2009-04-23
```

for m in {1..12}
do 
  for d in {1..31}
  do
     z=$(date "+%a" -d "2009-$m-$d") 
     case $z in
     Wed|Fri ) echo "2009-$m-$d: $z";;     
     esac
  done
done

```

---

### Post by Chokkan on 2009-04-24
Wow, thanks guys. :) What a fantastic response. This will all be really helpful, as I really had no idea how to do this. Let me see what I can do with the languages I'm more familiar with (Python). Anyone else can feel free to put their spin on things, the more the merrier. I'm far from a solution to this problem.

If any of you use the [**remind**]("http://linux.die.net/man/1/remind") program, I'm sure there is a way to do it via that as well.

Thanks again, you guys rock!

EDIT: 

OK, so with the Python script posted by croto, I send the ouput to a text file and then open it with Calc. This is almost perfect but Calc insists on adding a year to the date if I didn't specify one. This leads to incorrect data in every cell. Perhaps a new thread is better for that option.

What would be really cool is if the program would prompt me to enter which 2 days I want to use, and then produce the dates.

---

### Post by Chokkan on 2009-04-25
This is what I have so far. Input from the user, and output as a .csv file I can format with Calc. 

```
#!/usr/bin/env python

#This script takes a range of dates and two weekdays from the user. It then calculates the dates for all the weekdays in that range.

import datetime, sys

#This is the fuction that finds the dates for the weekdays specified. Credit to croto on the Ubuntu forums.
def get_weekday_dates(start, end, weekdays):
    delta = datetime.timedelta(1)
    dates = []
    while start<end:
        if start.weekday() in weekdays: dates.append(start)
        start += delta
    return dates

print "|||||||||||||||| The Date Script ||||||||||||||||\n"

#Which set of start and end dates will we use?
term = input("Please choose:\n1) First Term\n2) Second Term\n3) Third Term\n\nTerm: ")

if term == 1:
   start = datetime.date(2009,4,10)
   end = datetime.date(2009,6,25)
elif term == 2:
   start = datetime.date(2009,9,5)
   end = datetime.date(2009,12,27)
elif term == 3:
   start = datetime.date(2010,1,5)
   end = datetime.date(2010,3,20)

print "0) Monday"
print "1) Tuesday"
print "2) Wednesday"
print "3) Thursday"
print "4) Friday\n"

#Now we get the two days from the user, take all the data, and call our function.
days = get_weekday_dates(start, end, [input("Enter the first day: "),input("Now enter the second day: ")]);

#We then take the filename given at the command line for the name of the output file.
filename = sys.argv[1]
f = open(filename,"w") 

#I want to produce a .csv file with column headings "Date" and "Lesson".
f.write("Date,Lesson\n")

#Iterate over the dates and give us our output. Finally we write it to the file.
for date in days:
    output = date.strftime("%m/%d\n") # Output will be e.g 04/22
    f.write(output)
```

I'd really like to have the script produce a table I can just print out. What would be the best way to achieve this? My ideas are:

[LIST]
[*]ooolib-python    - Apparently can produce .ods files. Documentation seems to be non-existent, so is beyond my abilities.
[*]postscript         - Easiest option?
[/LIST]

---

### Post by Arndt on 2009-04-26
> **Chokkan said:**
> This is what I have so far. Input from the user, and output as a .csv file I can format with Calc. 
[...]
I'd really like to have the script produce a table I can just print out. What would be the best way to achieve this? My ideas are:

[LIST]
[*]ooolib-python    - Apparently can produce .ods files. Documentation seems to be non-existent, so is beyond my abilities.
[*]postscript         - Easiest option?
[/LIST]

I don't know what the best solution is, but here is one more suggestion: generate HTML, then view the file in a browser and let the browser print it.

Generating PDF is another way.

And generating TeX.

---

### Post by Chokkan on 2009-04-26
Thanks, those are all good options. I have been trying another avenue, which is to send the data to an openoffice writer table.

To do this, I'm using uno. I've managed to have it create the right number of rows in he table but I'm stuck at how to insert the data into the first column.

The current code:
```

#!/usr/bin/env python

# bootstrap uno component context     
import uno
import unohelper


# a UNO struct later needed to create a document
from com.sun.star.text.ControlCharacter import PARAGRAPH_BREAK
from com.sun.star.text.TextContentAnchorType import AS_CHARACTER
from com.sun.star.awt import Size


#This script takes a range of dates and two weekdays from the user. It then calculates the dates for all the weekdays in that range.

import datetime, sys

#This is the fuction that finds the dates for the weekdays specified. Credit to croto on the Ubuntu forums.
def get_weekday_dates(start, end, weekdays):
    delta = datetime.timedelta(1)
    dates = []
    while start<end:
        if start.weekday() in weekdays: dates.append(start)
        start += delta
    return dates

print "|||||||||||||||| The Date Script ||||||||||||||||\n"

#Which set of start and end dates will we use?
term = input("Please choose:\n1) First Term\n2) Second Term\n3) Third Term\n\nTerm: ")

if term == 1:
   start = datetime.date(2009,4,10)
   end = datetime.date(2009,6,25)
elif term == 2:
   start = datetime.date(2009,9,5)
   end = datetime.date(2009,12,27)
elif term == 3:
   start = datetime.date(2010,1,5)
   end = datetime.date(2010,3,20)

print "0) Monday"
print "1) Tuesday"
print "2) Wednesday"
print "3) Thursday"
print "4) Friday\n"

#Now we get the two days from the user, take all the data, and call our function.
days = get_weekday_dates(start, end, [input("Enter the first day: "),input("Now enter the second day: ")]);

#We then take the filename given at the command line for the name of the output file.
filename = sys.argv[1]
f = open(filename,"r+") 

#Iterate over the dates and give us our output. Finally we write it to the file.
for date in days:
    output = date.strftime("%m/%d\n") # Output will be e.g 04/22
    f.write(output)

fc = open(filename)
count=1
for line in fc.readlines():
    count+=1
#fc.close()
###################################################################

def insertTextIntoCell( table, cellName, text, color ):
    tableText = table.getCellByName( cellName )
    cursor = tableText.createTextCursor()
    cursor.setPropertyValue( "CharColor", color )
    tableText.setString( text )

localContext = uno.getComponentContext()
                   
resolver = localContext.ServiceManager.createInstanceWithContext(
                "com.sun.star.bridge.UnoUrlResolver", localContext )

smgr = resolver.resolve( "uno:socket,host=localhost,port=2002;urp;StarOffice.ServiceManager" )
remoteContext = smgr.getPropertyValue( "DefaultContext" )

#remoteContext = resolver.resolve( "uno:socket,host=localhost,port=2002;urp;StarOffice.ComponentContext" )
#smgr = remoteContext.ServiceManager

desktop = smgr.createInstanceWithContext( "com.sun.star.frame.Desktop",remoteContext)

# open a writer document
doc = desktop.loadComponentFromURL( "private:factory/swriter","_blank", 0, () )

text = doc.Text
cursor = text.createTextCursor()

# create a text table
table = doc.createInstance( "com.sun.star.text.TextTable" )

# with 4 rows and 4 columns
table.initialize( count, 2)


text.insertTextContent( cursor, table, 0 )
rows = table.Rows

table.setPropertyValue( "BackTransparent", uno.Bool(0) )
table.setPropertyValue( "BackColor", 13421823 )
row = rows.getByIndex(0)
row.setPropertyValue( "BackTransparent", uno.Bool(0) )
row.setPropertyValue( "BackColor", 6710932 )


textColor = 16777215


insertTextIntoCell( table, "A1", "Date", textColor )
insertTextIntoCell( table, "B1", "Lesson", textColor )

# This part is under construction. I want each line of the .csv file to go into the cells of the first column. I'm only getting one number in each column with this code :(

#table.getCellByName("A2").setValue(22.5)

cellnum = 1
for line in f.readlines():
   table.getCellByPosition(0,cellnum).setValue(line)
   cellnum+=1
   print line
#fc.close()

```

---

