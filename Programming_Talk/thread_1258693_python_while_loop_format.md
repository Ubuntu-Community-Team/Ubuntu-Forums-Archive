---
title: "python: while loop format"
date: 2009-09-05
forum: Programming Talk
---

### Post by filifunk on 2009-09-05
if you've seen me post before you know that I'm an uber beginner.  I have never learned any programming language before and have been working at python for the past couple weeks.  My question this time around pertains to while loops.

It is my understanding that while loops are in the format of:

```


while <expression>:
    <code block>


```

then I came across this while loop:

```



In [6]: string = "godzilla"

In [7]: while string:
   ...:     letter = string[0]
   ...:     print letter,
   ...:     string = string[1:]
   ...:     
   ...:     
g o d z i l l a


```

my question is how does 'while string:' in line 7 fit the format?  What is it testing in the expression.  This may seem like an elementary question, but I think you computer programmers just get this stuff naturally when I at this point would enjoy some explanation!  THANKS!

---

### Post by ghostdog74 on 2009-09-05
it just simply means while the variable "string" contains something, then do something. anyway, its not a best practice to name your variable to be the same as a Python library (ie. string). Also, its not "Pythonic" to get each letter of the variable like that. the for loop is better suited for this. 
```

mystring = "godzilla"
for i in mystring:
    print i,

```

---

### Post by filifunk on 2009-09-05
great, thanks.  So it will just keep going until there's something left in string which is getting progressively smaller through the loop.

---

