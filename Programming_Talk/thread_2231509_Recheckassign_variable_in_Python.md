---
title: "Recheck/assign variable in Python"
date: 2014-06-26
forum: Programming Talk
---

### Post by demontager on 2014-06-26
I am trying to assign variable in function, but when i call it doesn't work.
```

#!/usr/bin/python3
a = "This is a"
def test_b():
    b = "This is b"
    
print(a)
test_b()
print(b)    

``` 
So when i run it
```

 ./test.py 
This is a
Traceback (most recent call last):
  File "./test.py", line 8, in <module>
    print(b)    
NameError: name 'b' is not defined

```

or if i call like follows
print(test_b())

got None

---

### Post by spjackson on 2014-06-26
> **demontager said:**
> 
```

def test_b():
    b = "This is b"

``` 

b is local to the function test_b. Once test_b has exited, b no longer exists. If you want b to be global in order to use it outside of test_b then you need
```

def test_b():
    global b
    b = "This is b"

``` 
It is a good idea to avoid globals as much as possible, but it's ok as a learning exercise.

> 
or if i call like follows
print(test_b())

got None
You do not explicitly return a value from test_b, so the function returns None. If you want to use it like this, then you'd want test_b to be like this.
```

def test_b():
    b = "This is b"
    return b

```
or more simply
```

def test_b():
    return "This is b"

```

---

### Post by demontager on 2014-06-26
Thanks, your suggestons i used in real script and you told to avoid globals, so i used functions inside other function to call variable:
Helper function from which getting variable
```

def monif():
    MONIF = findall('mon[0-9]', str(check_output(['iwconfig'],stderr=DN)))
    if MONIF != []:
        return MONIF[0]
    else:
        return MONIF 


```
Main function:
```

def start():
    check_iface()
    if not 'mon0' in monif() and len(args) == 2:
        call(['airmon-ng', 'start', IFACE])
        call(['airodump-ng', '-w', DUMP, '--ignore-negative-one', monif()])
    elif not 'mon0' in monif() and len(args) == 3:
        call(['airmon-ng', 'start', IFACE, CH])
        call(['airodump-ng', '-w', DUMP, '-c', CH, '--ignore-negative-one', monif()])
    else:
        print(G+'Already has monitor mode'+W)

```

Is it fine to use such technic ? Actually script works as expected.

---

### Post by ofnuts on 2014-06-27
As a general rule, it's best if a function always return the same type of things. Your monif() funciton returns either a string (found something) or an array (found nothing). If you don't want to return anything, you can return "None" (without quotes).

---

### Post by spjackson on 2014-06-27
> **demontager said:**
> 
Is it fine to use such technic ?
I think so, yes. In some circumstances (e.g. if the monif function call is expensive), you might want to save its result to avoid calling it several times.
```

def start():
    check_iface()
    monif_result = monif()
    if not 'mon0' in monif_result and len(args) == 2:
        # etc. etc.

```

---

### Post by ofnuts on 2014-06-27
At that point one can also reconsider what the code really does, because getting all instances of mon[0-9], then keeping only the first one (why that one?), then looking if that first item contains 'mon0' (but since it's 'mon' followed by one single digit, if it contains 'mon0' then it is equal to it... why not simply make check_iface() return True/False if 'mon0 ' in 
str(check_output(['iwconfig'],stderr=DN)))?

---

