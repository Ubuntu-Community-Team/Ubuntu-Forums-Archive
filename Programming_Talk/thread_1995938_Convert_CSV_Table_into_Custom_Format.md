---
title: "Convert CSV Table into Custom Format"
date: 2012-06-03
forum: Programming Talk
---

### Post by ShareBuntu on 2012-06-03
Hello,

I've got a CSV file that I'd like to convert into a different format. The CSV format is as follows:

A_to_B,B_to_C,C_to_D,...
0,2,1,...

I.e., each heading consists of two variables, e.g. A and B, and each row in the file contains a value that is either 0, 1, or 2. I'm trying to write a Python script that'll read this CSV file and turn it into a format like this:

A,B,0
B,C,2
C,D,1
...

In other words, it splits the first line which consists of headers into variables (e.g., A, B, C, D, etc.) and then matches the corresponding value for the new format. Does anyone have any idea how to do this? I have some of the basics down, but the actual algorithm I can't get my head around properly. Thanks for your help.

---

### Post by shafi.dude99 on 2012-06-03
> **ShareBuntu said:**
> Hello,

I've got a CSV file that I'd like to convert into a different format. The CSV format is as follows:

A_to_B,B_to_C,C_to_D,...
0,2,1,...

I.e., each heading consists of two variables, e.g. A and B, and each row in the file contains a value that is either 0, 1, or 2. I'm trying to write a Python script that'll read this CSV file and turn it into a format like this:

A,B,0
B,C,2
C,D,1
...

In other words, it splits the first line which consists of headers into variables (e.g., A, B, C, D, etc.) and then matches the corresponding value for the new format. Does anyone have any idea how to do this? I have some of the basics down, but the actual algorithm I can't get my head around properly. Thanks for your help.

1)split and store the  header variables in an array
2) assign variable that wiil move around the array (eg : headernext=0)
3) repeat 
     write data as  "array[headernext],array[headernext+1],(scan line till comma) \n"
     until whole line is scanned

---

### Post by ShareBuntu on 2012-06-03
> **shafi.dude99 said:**
> 1)split and store the  header variables in an array
2) assign variable that wiil move around the array (eg : headernext=0)
3) repeat 
     write data as  "array[headernext],array[headernext+1],(scan line till comma) \n"
     until whole line is scanned
Can you give me a simple example of what that looks like in code? I'm somewhat challenged in that department. :oops:

---

### Post by shafi.dude99 on 2012-06-03
> **ShareBuntu said:**
> Can you give me a simple example of what that looks like in code? I'm somewhat challenged in that department. :oops:
i m not good at pyhton but i can try 
i actually dont know how to open file in pyhton but will able to help you with other logic

---

### Post by shafi.dude99 on 2012-06-03
f=open("ss.csv")
header=f.readline().split(',')
links=f.readline().split(',)
totalheader=len(header)
for index in range(totalheader-1)
     write data to file as
     "header[index],header[index+1],links[index]

---

### Post by ShareBuntu on 2012-06-03
> **shafi.dude99 said:**
> f=open("ss.csv")
header=f.readline().split(',')
links=f.readline().split(',)
totalheader=len(header)
for index in range(totalheader-1)
     write data to file as
     "header[index],header[index+1],links[index]
Thanks for this. After I ran that algorithm on a CSV file that looks like this:
```
A,B,C
0,2,1
0,1,1
```
I get this:
```
A,B,0
B,C
,2
```
I'm trying to figure it out on [this]("http://stackoverflow.com/questions/10874993/convert-csv-table-into-custom-format") Stack Overflow page too.

---

### Post by shafi.dude99 on 2012-06-04
> **ShareBuntu said:**
> Thanks for this. After I ran that algorithm on a CSV file that looks like this:
```
A,B,C
0,2,1
0,1,1
```I get this:
```
A,B,0
B,C
,2
```I'm trying to figure it out on [this]("http://stackoverflow.com/questions/10874993/convert-csv-table-into-custom-format") Stack Overflow page too.

yes there is problem ... as split also get '\n' with the last charachet

output of split will be : ['a','b','c\n'] u have to remove '\n '  

and run for loop upto totalheader

---

### Post by the_unforgiven on 2012-06-04
Python already comes with a module for [CSV parsing]("http://docs.python.org/library/csv.html").

After that, it's just how you create your data-structures ;)

Looking at your sample data, it seems like it provides mapping between some no. of entities.
Is it possible to have >1 rows? (i.e. the column A_to_B to have more than 1 values)?

If it's indeed a mapping like A->B, B->C, C->D etc., then you can simply create a two-dimensional list to store the values of individual mappings and then output in whatever format you want.

---

### Post by ShareBuntu on 2012-06-04
In case anyone wanted to see the solution, here's the code:
```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import csv,os,sys

reader = csv.reader(open(sys.argv[1], 'rt'), delimiter=',')
headers = reader.next()
i = 1

for row in reader:
    os.system('rm id' + str(i) + '.csv')
    os.system('cat ./seeds >> id' + str(i) + '.csv')
    for srcdest,dist in zip(headers, row):
        sd = srcdest.split('_to_')
        src,dest = sd[0],sd[-1]
        if dist == '0':
            pass
        else:
            f = open('id' + str(i) + '.csv', 'a')
            f.write('{},{},{}\n'.format(src.lower().replace('_',''),dest.lower().replace('_',''),float(dist)))
    i=i+1

f.close()
```It's rough, but it works! I will add some error handling to smooth it out a bit. Thanks again for your help!

---

