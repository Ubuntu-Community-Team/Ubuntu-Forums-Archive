---
title: "Python: bothering the crap out of me"
date: 2009-08-27
forum: Programming Talk
---

### Post by filifunk on 2009-08-27
Why is this bad syntax?

```


n = int(raw_input('What is n? ')
factorial = 1
for i in range(1, n + 1)
    factorial = factorial * i

print "factorial"


```

this is what I get when I run it through ipython:

WARNING: Failure executing file: <loops.py>

In [14]: run loops.py
------------------------------------------------------------
   File "loops.py", line 3
     factorial = 1
             ^
SyntaxError: invalid syntax

WARNING: Failure executing file: <loops.py>


why would 'factorial = 1' be bad syntax?  I'm just assigning it a number?

---

### Post by j.bell730 on 2009-08-27
> **filifunk said:**
> Why is this bad syntax?

```


n = int(raw_input('What is n? ')
factorial = 1
for i in range(1, n + 1)
    factorial = factorial * i

print "factorial"


```

this is what I get when I run it through ipython:

WARNING: Failure executing file: <loops.py>

In [14]: run loops.py
------------------------------------------------------------
   File "loops.py", line 3
     factorial = 1
             ^
SyntaxError: invalid syntax

WARNING: Failure executing file: <loops.py>


why would 'factorial = 1' be bad syntax?  I'm just assigning it a number?

You didn't close parentheses on your first line. Try this instead:
```
n = int(raw_input('What is n? '))
```

Also, you need to have a colon on this line, like this:
```
for i in range(1, n + 1):
```

EDIT- Just noticed something else...
```
print "factorial"
```
This will not print the variable, it will literally print "factorial".
Change that to:
```
print factorial
```

---

### Post by unutbu on 2009-08-27
Change
```
n = int(raw_input('What is n? ')

```to```

n = int(raw_input('What is n? '))
```

---

### Post by Bodsda on 2009-08-27
> **filifunk said:**
> 
why would 'factorial = 1' be bad syntax?  I'm just assigning it a number?

It is not actually complaining about that line. It is complaining that it was not expecting that line. As said by posters before me, it was failing due to inaccurate parenthesis closure.

---

