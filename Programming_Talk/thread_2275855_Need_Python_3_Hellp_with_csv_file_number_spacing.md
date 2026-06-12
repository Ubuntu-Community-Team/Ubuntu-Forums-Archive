---
title: "Need Python 3 Hellp with csv file number spacing"
date: 2015-04-28
forum: Programming Talk
---

### Post by lance bermudez on 2015-04-28
I have a csv file that has numbers in it that I would like to end with 2 decimal spaces.

idle code output
```

 S, LAST NAME, FIRST NAME, GRADE
 #S last_name first_name 765.198364389

 S, LAST NAME, FIRST NAME, GRADE
 #S last_name first_name 398.641946169

 S, LAST NAME, FIRST NAME, GRADE
 #S last_name first_name 722.164616977

 S, LAST NAME, FIRST NAME, GRADE
 #S last_name first_name 572.936356108

 S, LAST NAME, FIRST NAME, GRADE
 #S# Last First  644.746086957

 S, LAST NAME, FIRST NAME, GRADE
  #S# Last First  708.302443064

 S, LAST NAME, FIRST NAME, GRADE
  #S# Last First  138.822173913

 S, LAST NAME, FIRST NAME, GRADE
  #S# Last First  285.39

 S, LAST NAME, FIRST NAME, GRADE
  #S# Last First  268.598799172

```

python script
```

import csv
with open('/home/l_bermudez/Videos/11001.csv') as csvfile:
     reader = csv.DictReader(csvfile)
     for row in reader:
         print('\n',
               'S, Last name, First Name, Grade\n'.upper(),
               row['OrgDefinedId'],
               row['Last Name'],
               row['First Name'],
               str(row['Calculated Final Grade Numerator']).format('%.2f'))
               

```

thank you for your help. So if any one needs to copy this I ran into another error
```

>>> 
Traceback (most recent call last):
  File "C:\Users\lance\Videos\CSV_test0.py", line 10, in <module>
    '{:.2f}'.format(row['Calculated Final Grade Numerator']))
ValueError: Unknown format code 'f' for object of type 'str'

```

I did a google search and found out how to  fix it below is the working code without errors
```

import csv
with open('C:/Users/lance/Videos/11001.csv') as csvfile:
     reader = csv.DictReader(csvfile)
     for row in reader:
         print('\n',
               'S, Last name, First Name, Grade\n'.upper(),
               row['OrgDefinedId'],
               row['Last Name'],
               row['First Name'],
               '{:.2f}'.format(float(row['Calculated Final Grade Numerator'])))#this line has the fix for the error

```

---

### Post by Vaphell on 2015-04-29
you have it backwards. It's format_string.format( data_to_plug ) so you need to have {:.2f}.format( row[...] )

```
>>> row={'col1':'AAA', 'col2':'BBB', 'col3':'CCC', 'col4':3.345467}
>>> print( row['col1'], row['col2'], row['col3'], '{:.2f}'.format(row['col4'] ) )
AAA BBB CCC 3.35
```


That said you could format the whole thing instead of listing comma separated 'words'

```
>>> print( '{header}\n{col1} {col2} {col3} {col4:.2f}'.format( header='c1 c2 c3 c4'.upper(), **row ) )
C1 C2 C3 C4
AAA BBB CCC 3.35
```

when you use **dict in format(), it's as if you declared key=dict[key] for all keys, similar to the header definition. The keys become identifiers that can be used to name the placeholders in the format string. Using format() wholesale gives you more control over output formatting, because you can pad to width, align and what not.

---

