---
title: "python: list.remove(x)"
date: 2008-09-16
forum: Programming Talk
---

### Post by decoherence on 2008-09-16
Hi all! I'm only just getting in to Python programming. It seems quite nice and sane (especially coming from the world of bash scripting) but every now and then I get stuck.

I have a tab delimited 'database' that I'm trying to work with.

```
import sys
import csv

database=csv.reader(open('/var/www/ColourFlatPrinterDatabase.txt'), delimiter='\t')

for row in database:
        print row
```

gives me 

> 
...
['103', 'Music Room', 'NULL', 'MX9AH140TC', '610CL Deskjet', '51626A', '4', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL', 'NULL']
...

(among many others of course)

If I change that to

```
import sys
import csv

database=csv.reader(open('/var/www/ColourFlatPrinterDatabase.txt'), delimiter='\t')

for row in database:
        print row.remove("NULL")
```

I get "ValueError: list.remove(x): x not in list"

Can someone help a newbie out?

---

### Post by kjohansen on 2008-09-16
try NULL with no quotes in the remove statement...

---

### Post by LaRoza on 2008-09-16
Can't you just do:
```

database.remove("NULL")

```

---

### Post by days_of_ruin on 2008-09-16
```
import sys
import csv

database=csv.reader(open('/var/www/ColourFlatPrinterDatabase.txt'), delimiter='\t')

for row in database:
        print type(row)
```

If that doesn't give you ```
<type 'list'>
``` then don't try to do list operations on it.

Otherwise do what laroza said.

---

### Post by decoherence on 2008-09-16
okay, i'll try these things tomorrow! thanks for the replies:guitar:

---

### Post by Wybiral on 2008-09-16
BTW, the remove method of List removes only the first instance of it.

```

x = [1, 2, 3, 1, 2, 3]
x.remove(1)

# x is now [2, 3, 1, 2, 3]

```

And when 1 isn't in the list, such as:

```

x = [2, 3, 2, 3]
x.remove(1)

```

You get:

```

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: list.remove(x): x not in list

```

Try this:
```

not_null = (lambda x: not(x == 'NULL'))
without_nulls = (lambda x: filter(x, not_null))
database = map(without_nulls, database)

```

---

### Post by Quikee on 2008-09-17
> **Wybiral said:**
> 
```

not_null = (lambda x: not(x == 'NULL'))
without_nulls = (lambda x: filter(x, not_null))
database = map(without_nulls, database)

```

Why not just the good old list comprehension:

```
database = [i for i in database if i != 'NULL']
```

---

### Post by LaRoza on 2008-09-17
> **Quikee said:**
> Why not just the good old list comprehension:

```
database = [i for i in database if i != 'NULL']
```

Because he is a lisp fanboy :-)

---

### Post by Quikee on 2008-09-17
> **LaRoza said:**
> Because he is a lisp fanboy :-)

But isn't a ```
database = filter(lambda e: e != "NULL", database)
``` enough for a lisp fanboy then? :)

---

### Post by decoherence on 2008-09-17
List comprehension did the trick. Thanks's for pointing me in the right direction, Kenshin--er.. Quikee.

Here's the working code

```
#!/usr/bin/python

import sys
import csv

database=csv.reader(open('/var/www/ColourFlatPrinterDatabase.txt'), delimiter='\t')

for row in database:
        row = [i for i in row if i != 'NULL']
        print row
```

Produces

> ['103', 'Music Room', 'MX9AH140TC', '610CL Deskjet', '51626A', '4']

Thanks everyone!

---

### Post by Wybiral on 2008-09-17
> **Quikee said:**
> But isn't a ```
database = filter(lambda e: e != "NULL", database)
``` enough for a lisp fanboy then? :)

No, I was under the impression that the database was a two dimensional list. The original code was:

```

for row in database:
        print row.remove("NULL")

```

(which looks to me like: for each list in database, remove from list)

So if it were 2-dimensional, wouldn't it be:

```

database = [[i for i in row if i != 'NULL'] for row in database]

```

Call me a Lisp fanboy if you want :) but I can't stand nested LC (this one isn't bad, but as a general rule). But anyway, you're right, LC is way more Pythonic than map/filter.

---

### Post by decoherence on 2008-09-17
I'm still not sure why it gave me "ValueError: list.remove(x): x not in list" for ```
for row in database:
        print row.remove("NULL")
```

using ```
print type(row)
``` indicated that each row is a list and they definitely have a NULL string in 'em... even if it would only catch the first one it seems to me like it should work.

can anyone explain why it doesn't (or if it even should? or if it's probably a pebcak?) and perhaps help increase my python kung fu? I can supply a sterilized source file if you want, but it's just a tab delimited list of records (two-dimensional, spreadsheet, worksheet, table, whatever you like)

I went with LC because it was easier for me to understand at a glance (haven't worked with lambda yet)

thanks again!

---

### Post by Wybiral on 2008-09-17
> **decoherence said:**
> can anyone explain why it doesn't (or if it even should? or if it's probably a pebcak?)

Reread the beginning of my first reply ;)

Hint: it's not a "remove all" or "remove if exists" it's a "remove first, always"

---

### Post by decoherence on 2008-09-17
> **Wybiral said:**
> Reread the beginning of my first reply ;)

Hint: it's not a "remove all" or "remove if exists" it's a "remove first, always"

I must be mis-understanding... You seem to be saying list.remove("foo") will only work if "foo" is the first item in the list? But then, shouldn't this give us the "list.remove(x): x not in list" error?

```
x = [1, 2, 3, 1, 2, 3, 1]
print(x)
x.remove(1)
print(x)
x.remove(1)
print(x)
```

it seems to work like I initially expected it to when I was trying to strip NULLs... i'm confused...

---

### Post by days_of_ruin on 2008-09-17
> **decoherence said:**
> I must be mis-understanding... You seem to be saying list.remove("foo") will only work if "foo" is the first item in the list? But then, shouldn't this give us the "list.remove(x): x not in list" error?

```
x = [1, 2, 3, 1, 2, 3, 1]
print(x)
x.remove(1)
print(x)
x.remove(1)
print(x)
```

it seems to work like I initially expected it to when I was trying to strip NULLs... i'm confused...

Does every row have "NULL" in it?Try printing each row.

---

### Post by decoherence on 2008-09-17
> **days_of_ruin said:**
> Does every row have "NULL" in it?Try printing each row.

Hmm, I think you figured it out. I'm not at work now but I'll check tomorrow.

In the source file, the very first record is a header for each column, to make it more human readable. Thus it has no "NULL" string, which explains why the thing dies right off the bat.

I neglected to mention that vital piece of information (sorry everyone,) but I'm pretty sure you snuffed it. It was a pebcak, as it surely must be with a newb learning python!:lolflag:

Thanks!

---

### Post by Wybiral on 2008-09-17
> **decoherence said:**
> I must be mis-understanding... You seem to be saying list.remove("foo") will only work if "foo" is the first item in the list? But then, shouldn't this give us the "list.remove(x): x not in list" error?

No, I was saying that remove only removes the first instance of x in the list, and that it ALWAYS removes the first instance of x in the list (hence, when there is no x, you have a problem).

---

### Post by decoherence on 2008-09-17
> **Wybiral said:**
> No, I was saying that remove only removes the first instance of x in the list, and that it ALWAYS removes the first instance of x in the list (hence, when there is no x, you have a problem).

ah, my confusion had abated! thanks for your patience.

---

### Post by decoherence on 2008-09-18
Finally, for posterity, the working version of what I was trying in the first place

```
for row in database:
        if "NULL" in row:
            row.remove("NULL")
            print row
```

So simple! Now the error makes perfect sense -- remove() can't remove something that isn't there! All I needed was the extra conditional to test for NULL in the first place.

ADD: hmm... on further inspection i may be wrong.

```
for row in setVars.database:
        while "NULL" in row:
            row.remove("NULL")
        print row
```

this seems more like it... gets rid of all the NULLs, keeps things in list form. Now I know something about the difference between 'while' and 'for'! :guitar:

---

