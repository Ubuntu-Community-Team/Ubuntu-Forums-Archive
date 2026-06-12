---
title: "python calculator help"
date: 2008-06-26
forum: Programming Talk
---

### Post by MDSmith2 on 2008-06-26
Hello, I am wanting to make a basic (+-*/ only) python calculator that will exit when you type quit.
the problem is when i use raw_input("") it will only take the quit command and won't add up the numbers but when i use int(raw_input("") it will only work with the numbers.
heres the code:
```
#!/usr/bin/python
import os
runing = True
os.system("clear")
print "Calulator Program \
by Michael Smith"
print "Type q to exit"
while runing:
      a = int(raw_input(""))
      if a == 'q':
        break
      b = int(raw_input(""))
      if b == 'q':
       break
      c = int(raw_input(""))
      if c == 'q':
       break
      if b == '+':
       d = a+c
      elif b == '-':
       d = a-c
      elif b == '*':
       d = a*c
      elif b == '/':
       d = a/c
      else:
       print "Invaild option!" 
```

---

### Post by LaRoza on 2008-06-26
> **MDSmith2 said:**
> Hello, I am wanting to make a basic (+-*/ only) python calculator that will exit when you type quit.
the problem is when i use raw_input("") it will only take the quit command and won't add up the numbers but when i use int(raw_input("") it will only work with the numbers.
heres the code:


Get the input and handle it after.


Examples:
```

ops = ("+","-","*","/")

x = raw_input("")
if x.upper() in ("EXIT","QUIT"):
    break
elif x.isdigit():
    print "X is a digit!"
elif x in ops:
    print "X is an operation!"
else:
    print "Error"

```

---

