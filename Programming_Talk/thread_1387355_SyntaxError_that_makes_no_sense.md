---
title: "SyntaxError that makes no sense"
date: 2010-01-21
forum: Programming Talk
---

### Post by epicoder on 2010-01-21
Sorry, forgot to put in the title that the language is python 2.6.

Here is my program in full:
```
raw_input('I am going to show you 6 groups of numbers. [press enter]')
print 
print 'Group 1:'
print '1 3 5 7 9 11 13 15'
print '17 19 21 23 25 27 29 31'
print '33 35 37 39 41 43 45 47'
print '49 51 53 55 57 59 61 63'
raw_input('[press enter]')
print
print 'Group 2:'
print '2 3 6 7 10 11 14 15'
print '18 19 22 23 26 27 30 31'
print '34 35 38 39 42 43 46 47'
print '50 51 54 55 58 59 62 63'
raw_input('[press enter]')
print
print 'Group 3:'
print '4 5 6 7 12 13 14 15'
print '20 21 22 23 28 29 30 31'
print '36 37 38 39 44 45 46 47'
print '52 53 54 55 60 61 62 63'
raw_input('[press enter]')
print
print 'Group 4:'
print '8 9 10 11 12 13 14 15'
print '24 25 26 27 28 29 30 31'
print '40 41 42 43 44 45 46 47'
print '56 57 58 59 60 61 62 63'
raw_input('[press enter]')
print
print 'Group 5:'
print '16 17 18 19 20 21 22 23'
print '24 25 26 27 28 29 30 31'
print '48 49 50 51 52 53 54 55'
print '56 57 58 59 60 61 62 63'
raw_input('[press enter]')
print
print 'Group 6:'
print '32 33 34 35 36 37 38 39'
print '40 41 42 43 44 45 46 47'
print '48 49 50 51 52 53 54 55'
print '56 57 58 59 60 61 62 63'
raw_input('[press enter]')
print
cards=['placeholder', 1, 2, 4, 8, 16, 32]
print 'Pick a number from the groups above.'
epicfail=False
while 1:
    if epicfail==True:
        ucards=raw_input('Please enter group numbers. E.G, \'4, 5, 6\', not \'8, 16, 32\' '
        epicfail=False
    else:
        ucards=raw_input('Enter the numbers of the groups that contain your number: ')
    ucards=ucards.replace(' ', '')
    ucards=ucards.replace(',', '')
    ucards=list(ucards)
    total=0
    for x in ucards:
        try:
            total=total+cards[int(x)]
        except:
            epicfail=True
            break
    if epicfail==True:
        place='holder'
    else:
        break
print 'Your number is ' + str(total)
```I keep getting this error:
```
/usr/bin/python -u  "/home/sh228/Desktop/magictrick.py"
  File "/home/sh228/Desktop/magictrick.py", line 51
    epicfail=False
           ^
SyntaxError: invalid syntax
```

---

### Post by sisco311 on 2010-01-21
```

while 1:
    if epicfail==True:
        ucards=raw_input('Please enter group numbers. E.G, \'4, 5, 6\', not \'8, 16, 32\' '**)** 
        epicfail=False
    else:

```

---

### Post by epicoder on 2010-01-21
Nice spot, thanks. Interesting that it complains about the above line, though.

---

### Post by jflaker on 2010-01-21
== is compare
= assigns value

---

### Post by epicoder on 2010-01-21
Recount your line numbers.

---

### Post by sisco311 on 2010-01-21
> **sh228 said:**
> Nice spot, thanks. Interesting that it complains about the above line, though.

The syntax error is at line 51.

You don't have to close the bracket at line 50 
```
print("text1"
"text2"
"text3")
```

---

