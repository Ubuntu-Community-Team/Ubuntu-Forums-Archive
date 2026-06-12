---
title: "question about Python"
date: 2013-01-13
forum: Programming Talk
---

### Post by daviddoji on 2013-01-13
I want to be asked when I run this for "enter an integer" and, after that, the code would still run the definition.
Here is my code
```
x = int(raw_input('Enter an integer: '))
def fib(x):
        """Assumes x an int >= 0
           returns Fibonacci of x"""
        assert type(x) == int and x >= 0
        if x == 0 or x == 1:
            return 1
        else:
            return fib(x-1) + fib(x-2)
```

With this code, I'm asked for enter the integer, but it stops!
If I want to execute the function, I have to type in the shell: 
```
fib("number")
```

How can I make it?

P.S.: Sorry for my English!

---

### Post by SGFzc2U= on 2013-01-13
If I understood correctly, you want this:
```

def fib(x):
        """Assumes x an int >= 0
           returns Fibonacci of x"""
        assert type(x) == int and x >= 0
        if x == 0 or x == 1:
            return 1
        else:
            return fib(x-1) + fib(x-2)
x = int(raw_input('Enter an integer: '))
print fib(x)

```

---

### Post by daviddoji on 2013-01-13
> **SGFzc2U= said:**
> If I understood correctly, you want this:
```

def fib(x):
        """Assumes x an int >= 0
           returns Fibonacci of x"""
        assert type(x) == int and x >= 0
        if x == 0 or x == 1:
            return 1
        else:
            return fib(x-1) + fib(x-2)
x = int(raw_input('Enter an integer: '))
print fib(x)

```

Exactly!

Thanks a lot!

---

### Post by trent.josephsen on 2013-01-13
Tangential, but it's usually advisable not to do this:

```
assert type(x) == int
```

Just let x be whatever type it really is, and allow the function to raise an error if the operations you try to do on it can't be done. Python's type system is strong, so you won't accidentally do fib('2') or fib(1.5) and not notice the problem. If another function could accidentally pass a non-number sometimes, that's something you should find when testing that other function (and probably a symptom of a real design flaw).

---

