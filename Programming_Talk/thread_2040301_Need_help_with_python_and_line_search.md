---
title: "Need help with python and line search"
date: 2012-08-10
forum: Programming Talk
---

### Post by MadsRC on 2012-08-10
I've recently started learning Python, and sofar things are going well...

I'm stuck on this bit though.
I got a file formated like this:
```
----
Info 1: Salmon
Info 2: Fish
Info 3: Food
----
Info 1: Pepsi
Info 2: Liquid
Info 2: Beverage
----
```

What I want to do, is search for a string, say "Fish" and the print the line that matches, plus the 2 lines above and the 2 lines bellow, so that searching for the string "Fish" would print:
```
----
Info 1: Salmon
Info 2: Fish
Info 3: Food
----
```

I've been messing around with the code, and have tried to utilise file.readline() and file.readlines(), file.seek and file.tell, to somehow establish the "cursor" location to be where the line containing the string is, and the move the cursor 2 lines up, and then printing that line (which would then be the top ----) and the next 5 lines (the last one being the last ----).

I must be doing something wrong? Could anybody help me out?
It's late around here, I'll get some sleep and hopefully I'll figure out a way tommorow...

---

### Post by era86 on 2012-08-10
What are you thinking as far as algorithm goes? Taking a naive approach, mine would look something like...

[PHP]
Define an array that stores 2 objects

Open file and do this until end of file
    Read in a line
    Search for substring in that line
    If no match
        Store it in the array
        Continue to next line
    If match
        Print out stored lines (if any) 
        Print out next two lines
        Exit
[/PHP]

Hope this helps.

---

### Post by Jacobonbuntu on 2012-08-10
> **MadsRC said:**
> I've recently started learning Python, and sofar things are going well...

I'm stuck on this bit though.
I got a file formated like this:
```
----
Info 1: Salmon
Info 2: Fish
Info 3: Food
----
Info 1: Pepsi
Info 2: Liquid
Info 2: Beverage
----
```What I want to do, is search for a string, say "Fish" and the print the line that matches, plus the 2 lines above and the 2 lines bellow, so that searching for the string "Fish" would print:
```
----
Info 1: Salmon
Info 2: Fish
Info 3: Food
----
```I've been messing around with the code, and have tried to utilise file.readline() and file.readlines(), file.seek and file.tell, to somehow establish the "cursor" location to be where the line containing the string is, and the move the cursor 2 lines up, and then printing that line (which would then be the top ----) and the next 5 lines (the last one being the last ----).

I must be doing something wrong? Could anybody help me out?
It's late around here, I'll get some sleep and hopefully I'll figure out a way tommorow...

You forget to say if it is python 2.x or 3.x, but if the file would be "test.txt", and it would be in "path-to-file/test.txt", in python3 this example would work. I am not sure if this is what you mean?

[PHP]
#!/usr/bin/python3

f = open("path-to-file/test.txt")
filetest = f.readlines()
f.close()

for line in filetest:
    if "Fish" in line:
        line_index = filetest.index(line)
        print_job =[filetest[line_index-1],
                    filetest[line_index],
                    filetest[line_index+1]]
        for item in print_job:
            print(item, end="")[/PHP]

However, I get the feeling you are trying to creat a database, which has much more convenient solutions than this one :)

---

### Post by trent.josephsen on 2012-08-10
print() takes multiple arguments and separates them on output with the value of the keyword parameter 'sep' (which defaults to ' '). I'd probably write that as follows.

```
for index in range(len(filetest)):
    if 'Fish' in filetest[index]:
        print(  filetest[index - 1],
                filetest[index    ],
                filetest[index + 1],
                sep='', end='' )
```

I understand why you would want to use Python's list.index() method to get the index of the line, but that introduces at least one obvious bug (when the same line occurs twice), quite apart from performance issues.

---

### Post by Jacobonbuntu on 2012-08-11
> **trent.josephsen said:**
> I understand why you would want to use Python's list.index() method to get the index of the line, but that introduces at least one obvious bug (when the same line occurs twice), quite apart from performance issues.

true of course

---

### Post by Some Penguin on 2012-08-11
If the input contains:
----
blah0
blah1
blah2
query string
query string
blah3
blah4
query string
blah5
blah6
blah7
---

what is the desired output?  The simplest approach includes lines being emitted multiple times (e.g. blah3 is at most two lines away from each of the three matches), but with a handful of states and it's not hard to have it omit each line at most once (e.g. blah1 -> blah6 inclusive, once each).

---

