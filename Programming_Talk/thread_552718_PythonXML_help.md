---
title: "Python/XML help"
date: 2007-09-16
forum: Programming Talk
---

### Post by IDipSkoalMint on 2007-09-16
Hey all. I have a little python program that I need to parse through an .xml file and print out information. The assignment is as followed:

> # Using only regular expression to identify the tags and data, write a Python script or Ruby script which

    1) -- reads a xml "check book" (ascii) file 
        -- prints out the payee's name (the string between <payee> tags),  
    2) -- reads an xml "check book" (ascii) file
        -- prints out the check number  (value of the number attribute  between the <payment> tag)
        -- if the amount is less than $100 print the value (the value between the <amount> tag)

I have the following .py file (attached) that goes as followed:

```
import os

file = open('checkbook.xml')
text = file.read()
lines = text.split('\n')

import re

patStrA = "<payee>(.*)<\/payee>"
patStrB = "<payment>(.*)<\/payment>" # This is wrong - I'm looking to store the check number, which is in the form <payment type="check" number="[number I want]">
patStrC = "<amount>\$(.*)<\/amount>"

patObjA = re.compile(patStrA)
patObjB = re.compile(patStrB)
patObjC = re.compile(patStrC)

i = 0
for line in lines:
        i = i + 1
        resultObjA = patObjA.search(line)
        resultObjB = patObjB.search(line)
        resultObjC = patObjC.search(line)
        if resultObjA:
                print 'Payee: ' + resultObjA.group(1)
        if resultObjB:
                c = float(resultObjB.group(1))
                print 'Check #: ' + resultObjB.group(1)
        if resultObjC:
                p = float(resultObjC.group(1))
                if p < 100.00: 			 
                        print 'Price: $' + resultObjC.group(1)
```

Also attached is the .xml file that needs to be parsed and the assignment.

TIA for your help.

---

### Post by cwaldbieser on 2007-09-16
You would be better off using one of the XML parsing libraries for python, like elementTree, or minidom.

---

### Post by ghostdog74 on 2007-09-17
Using regular expression? Here's one without regexp. all making use of Python's powerful string functions.
```

for line in open("checkbook.xml"):
    line=line.strip()
    if line.startswith("<payee>"):
        print line.replace("<payee>","").replace("</payee>","")        
    if line.startswith("<payment type=\"check\""):
        numindex=line.find("number")
        print line[numindex+len("number=\""):].rstrip("\">")
    if line.startswith("<amount>"):
        amt = line.replace("<amount>","").replace("</amount>","")
        if float(amt) > 100:
            print amt

```
However, since this is your assignment and its using regexp, here's an example snippet..adapt to your needs
```

pat = re.compile("<payment type=\".*number=\"(.*?)\">")
for line in open("checkbook.xml"):
   print pat.findall(line)


```

---

### Post by pmasiar on 2007-09-17
ElementTree is best XML parser - try it.

---

