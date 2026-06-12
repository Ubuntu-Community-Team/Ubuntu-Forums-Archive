---
title: "optimising silly python table program"
date: 2008-11-10
forum: Programming Talk
---

### Post by ingo on 2008-11-10
Hi,

complete newbie to programming fighting my way through "Thinking like a python programmer". Below is a program to draw a table. 

I am not pleased with the last three lines of the main function:
 tableh(a)
tableh(a)
column(a)

Any ideas of how to optimise this?

```
def table(a):
    def column(a):
        print '+','- '*a+'+','- '*a+'+'
        return
    def row(a):
        print ' |',' '*a*2,'|',' '*a*2,'|'
        return
    def tableh(a):
        for b in range(a):
            if b==0:
                column(a)
            else:
                row(a)
        return
    tableh(a)
    tableh(a)
    column(a)
    return
a=input("gissa a number then: ")
table(a)
```Many thanks in advance for any hints/suggestions/ideas :)

---

### Post by geirha on 2008-11-10
How about something like this?
```
for i in range(a*2):
  if i % a == 0: column(a)
  else: row(a)
column(a)

```

Btw, you should use raw_input instead of input. input is not safe.

---

### Post by ingo on 2008-11-10
Wow, that is stuff I haven't come across yet, in particular % - I'll be on the lookout for that one :)

Reason I used input was to get an integer, raw_input produces a type error.

---

### Post by elbarto_87 on 2008-11-10
> **ingo said:**
> Wow, that is stuff I haven't come across yet, in particular % - I'll be on the lookout for that one :)

Reason I used input was to get an integer, raw_input produces a type error.

You can use the int() function to convert raw_input to an integer


```
a = raw_input("Enter a number:")
a = int(a)
```

Obviously that piece of code is pretty trivial but it might help you out in something else....

---

### Post by geirha on 2008-11-10
Also, to make it even shorter, instead of using functions to print one line, just store column and row in a string, then print that string later

```

def table(a):
    column='+ '+'- '*a+'+ '+'- '*a+'+'
    row='| '+' '*a*2+'| '+' '*a*2+'|'
    for i in range(a*2): print i % a == 0 and column or row
    print column

```

The % operator gives you the remainder in integer division. E.g. 5 divided by 3 is 1 with a remainder of 2, so
```
>>> 5/3
1
>>> 5%3
2

```

To use raw_input to get an int, do something like:
```
a=raw_input("gissa a number then: ")
try:
   a= int(a)
   table(a)
except ValueError:
   print "Not a valid integer"

```

---

### Post by ingo on 2008-11-10
Thank you very much, that has shrunk the program quite a bit :) Why I didn't think that column and row could be simple strings I'll never know :D

---

### Post by ingo on 2008-11-10
[FONT=monospace][SIZE=3][FONT=Verdana]Actually, I'm still chewing over this line[/FONT]

[/SIZE][/FONT]> [FONT=monospace][SIZE=3]for i in range(a*2): print i % a == 0 and column or row[/SIZE][/FONT][SIZE=3]If I understand it correctly, it works like this: 

If[/SIZE][SIZE=3] the value after the print command is 0, the "and" causes a column to be printed while other values result in rows 

I have never come across that notation - cool![/SIZE]

---

### Post by geirha on 2008-11-10
Yes, be a bit careful when using it though. For instance, empty sequences and empty strings are considered False. [http://diveintopython.org/power_of_introspection/and_or.html](http://diveintopython.org/power_of_introspection/and_or.html)

---

