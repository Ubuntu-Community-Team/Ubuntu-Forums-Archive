---
title: "With python3 How do I search a csv ditreader for only the name I want?"
date: 2015-05-02
forum: Programming Talk
---

### Post by lance bermudez on 2015-05-02
I have a grade book that is in csv from desire2learn. I want to have a python3 script read the file with csv.distreader because I do not want to count the 1,000 + row. From this script I can print out only the columns with the data I want but I want to know how to just get one student row['OrgDefinedId'] matching the data in '{:.2f}'.format(float(row['Calculated Final Grade Numerator']))).

the data in the   row['OrgDefinedId']  has data looking like #S00012345 this is what I want to put the input funttion to get the student grade from '{:.2f}'.format(float(row['Calculated Final Grade Numerator'])))
 
```

import csv
with open('11001.csv') as csvfile:
     reader = csv.DictReader(csvfile)
     for row in reader:
         print('\n',
               'S, Last name, First Name, Grade\n'.upper(),
               row['OrgDefinedId'],
               row['Last Name'],
               row['First Name'],
               '{:.2f}'.format(float(row['Calculated Final Grade Numerator'])))

```

What I want to print out from my grade book is just want the final grade with 2 decimanl places to mach the 'OrgDefinedId' I put in by using the input command.
code

---

### Post by Vaphell on 2015-05-02
```
if row['OrgDefinedId'] == student:
    print( stuff )
```

?

that said maybe you should consider slurping all students from the file and dumping them to an easily accessible dictionary so you don't have to read a file every time you want something.
It could look something like this

```
students = {}

with open('11001.csv') as csvfile:
    reader = csv.DictReader(csvfile)
    for row in reader:
        s_id = row['OrgDefinedId']
        last = row['Last Name']  
        first = row['First Name']
        grade = float( row['Calculated Final Grade Numerator'] )
        students[s_id] = last, first, grade        # last, first and grade saved as a tuple under s_id key


selected_student = input('id? ')
if selected_student in students:
    last, first, grade = students[selected_student]
    print( selected_student, last, first, grade )
else:
    print('no such student' )
```

---

