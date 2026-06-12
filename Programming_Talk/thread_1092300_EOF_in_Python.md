---
title: "EOF in Python"
date: 2009-03-10
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-03-10
Suppose if i want to break out of a loop when the input given is the EOF then what will the conditional statement be.
i=input("")

if i=="EOF":
         break

Will this work

---

### Post by ghostdog74 on 2009-03-10
2 ways to iterate files
1) for loop
```

for line in open("file"):
  print line

```
2) while loop
```

f=open("file")
while 1:
  line=f.readline()
  if not line: break
  print line  
f.close()

```

---

### Post by LegendofTom on 2009-03-10
If you iterate by line, the end of the file should be the end of the loop.

---

### Post by WW on 2009-03-10
One method is to catch the EOFError exception that will be raised:
```

>>> while True:
...     try:
...         s = raw_input("What is your name? ")
...     except EOFError:
...         print
...         print "Bye."
...         break
...     print "Hello, %s" % s
... 
What is your name? WW
Hello, WW
What is your name? 
Bye.
>>> 

```
I hit control-D at the second prompt.

---

### Post by 7raTEYdCql on 2009-03-10
inputfile.readline() automatically detects the end of file, when inputfile is opened in read ony mode???

---

### Post by 7raTEYdCql on 2009-03-10
My question is not about reading files.

I want to get input from terminal screen only, and i want to exit the loop of the program when ctrl+d(EOF) is typed. How is that done.

---

### Post by 7raTEYdCql on 2009-03-10
Stupid question. I think the program automatically terminates when i press ctr+d.

Thanks anyway.

---

### Post by 7raTEYdCql on 2009-03-10
No but i get a error when i press ctrl+d

How do i avoid this error??

---

### Post by WW on 2009-03-10
Reread my post above. :)

It works with input() as well as raw_input().

---

### Post by slavik on 2009-03-10
> **WW said:**
> One method is to catch the EOFError exception that will be raised:
```

>>> while True:
...     try:
...         s = raw_input("What is your name? ")
...     except EOFError:
...         print
...         print "Bye."
...         break
...     print "Hello, %s" % s
... 
What is your name? WW
Hello, WW
What is your name? 
Bye.
>>> 

```
I hit control-D at the second prompt.
will this setup a try/catch block on ever loop iteration?

---

### Post by WW on 2009-03-10
> **slavik said:**
> will this setup a try/catch block on ever loop iteration?
Sorry, I don't understand your question.  The code catches the EOFError exception that is raised when ctrl-D is entered.  The code in the 'except' block includes a 'break' statement, which exits the while loop.

---

### Post by danielgenin on 2012-04-26
> **WW said:**
> Sorry, I don't understand your question.  The code catches the EOFError exception that is raised when ctrl-D is entered.  The code in the 'except' block includes a 'break' statement, which exits the while loop.

Would it make more sense to enclose the whole while loop in try ... except, rather than having the except clause in the body  of the while loop?

---

