---
title: "how to I write python 3 csv file dictreader to dict writer"
date: 2015-04-30
forum: Programming Talk
---

### Post by lance bermudez on 2015-04-30
Ok what i want to do is take the info out the print function and put it into another csv file.

python3 script
```

import csv
with open('C:/Users/lance/Videos/11001.csv') as csvfile:
     reader = csv.DictReader(csvfile)
     for row in reader:
#I want this print fieldnames written to another file with the data.
         print('\n',
               'S, Last name, First Name, Grade\n'.upper(),
               row[[COLOR="#FF0000"]'OrgDefinedId'[/COLOR]],
               row[[COLOR="#FF0000"]'Last Name'[/COLOR]],
               row[[COLOR="#FF0000"]'First Name'[/COLOR]],
               '{:.2f}'.format(float(row[[COLOR="#FF0000"]'Calculated Final Grade Numerator[/COLOR]'])))[COLOR="#FF0000"]#this line has to keep its formatting[/COLOR]

```

I'm stuck I do not know how to proceed. Was thinking of something like this
```

import csv
import operator

with open('C:/Users/lance/Videos/11001.csv') as csvfile:
     reader = csv.DictReader(csvfile)     
     for row in reader:
         snumber = row['OrgDefinedId']
         last = row['Last Name']
         first = row['First Name']
         grade = '{:.2f}'.format(float(row['Calculated Final Grade Numerator']))
         print(snumber)

         csvfile = open('eggs.txt','w')
         csvfile.write (snumber)
         csvfile.write (',')

```
But this does not write out all the snumber that is seen in the print just the first line.

---

### Post by Vaphell on 2015-04-30
you are opening the file for each line and do so the 'w' flag which is overwrite instead of append ('a')

```
with open( 'out.txt', 'w' ) as ofile:
    with open( 'in.txt' ) as ifile:
        for line in ifile:
            ofile.write( line )
```

edit: you are using the same file (csvfile) but the comment says you want output in another file?

---

