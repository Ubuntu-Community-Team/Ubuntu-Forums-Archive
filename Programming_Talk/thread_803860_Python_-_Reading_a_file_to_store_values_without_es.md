---
title: "Python - Reading a file to store values without escaped characters"
date: 2008-05-22
forum: Programming Talk
---

### Post by ConMan318 on 2008-05-22
Alright, so I am writing a program that converts Roman numerals to decimals, reading from a file of Roman numerals in this type of format:
```

XII
XVII
MXLI

```

I already have a function written that converts a string like 'XVII' to its decimal equivalent, and it works perfectly.  The problem is in reading the file, it stores '\r\n' at the end of each one.  First of all, why does it store two different types of newlines after each numeral?

Second, no matter how I try to split the numerals, I can't seem to get rid of those characters entirely; it always manages to store one of them in the string, which screws up my function, which only works with strings that are passed like toDecimal('XVII').

This is the base code I have been messing around with to try to eliminate the newlines:
```

f = open("file.txt", "r").readlines()
for numeral in f:
    for token in numeral.split('\n'):
        print token, toDecimal(token)

```

I have tried to replace the split character with '\r\n'; I have added another nested 'for' loop with one splitting the \r's and the other splitting the \n's.  Nothing I have done works.

Even when I remove the function call in the above code, when it prints the numerals, it prints like this:
```

XII

XVII

MXLI


```
with two carriage returns between each one.

Any help would be greatly appreciated; I feel like I'm missing some small tweak that would fix it up easily.

---

### Post by Can+~ on 2008-05-22
[FONT="Courier New"]astring.rstrip()[/FONT]

In fact, you should use [FONT="Courier New"]strip()[/FONT] to remove any undesired character.


[PHP]romanfile = open("file.txt", "r")

for line in romanfile:
    print line.strip()[/PHP]

---

### Post by ConMan318 on 2008-05-22
Worked perfectly, thank you very much.

---

