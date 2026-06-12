---
title: "Python exceptions: retry on transient errors"
date: 2008-04-23
forum: Programming Talk
---

### Post by mssever on 2008-04-23
Suppose I get an exception due to a transient error such as a network glitch. In Ruby, I might do something like this:
```
counter = 0
begin
  foo.bar
rescue SomeTransientError
  counter += 1
  if counter < 10
    retry
  else
    raise
  end
end
```Where retry jumps to the begin. What's the recommended way to do this in Python?

---

### Post by ghostdog74 on 2008-04-23
> **mssever said:**
> Suppose I get an exception due to a transient error such as a network glitch. In Ruby, I might do something like this:
```
counter = 0
begin
  foo.bar
rescue SomeTransientError
  counter += 1
  if counter < 10
    retry
  else
    raise
  end
end
```Where retry jumps to the begin. What's the recommended way to do this in Python?

```

try
  ...
except Exception,e: 
  ...

```

---

### Post by Quikee on 2008-04-23
> **mssever said:**
> Suppose I get an exception due to a transient error such as a network glitch. In Ruby, I might do something like this:
```
counter = 0
begin
  foo.bar
rescue SomeTransientError
  counter += 1
  if counter < 10
    retry
  else
    raise
  end
end
```Where retry jumps to the begin. What's the recommended way to do this in Python?

[PHP]
counter = 0
while counter < 10:
    try:
        foo.bar
    except SomeTransientError:
        counter += 1
        if counter >= 10:
            raise[/PHP]
:)

---

### Post by RIchard James13 on 2008-04-23
Maybe like this
[PHP]        fails = 0
        passed = 0
        while passed==0 or fails<10:
            try:
                someFunctionThatFails()
                passed=1
            except:
                fails+=1
                
        if passed!=1:
            raise someException
[/PHP]

---

### Post by RIchard James13 on 2008-04-23
> **Quikee said:**
> [PHP]
counter = 0
while counter < 10:
    try:
        foo.bar
    except SomeTransientError:
        counter += 1
        if counter >= 10:
            raise[/PHP]
:)

Actually I thought of that but then realised that if the exception is never triggered then foo.bar will be called forever.

I think what we want here is 
Function is called
If it errors then retry up to ten times
Else continue with the program

---

### Post by Quikee on 2008-04-23
> **RIchard James13 said:**
> Actually I thought of that but then realised that if the exception is never triggered then foo.bar will be called forever.

Damn.. I totally overlooked this case. ;)

---

### Post by mssever on 2008-04-23
So Python basically makes you use a while loop? I suspected that that might be the case, but I was hoping I was wrong. Ruby's retry statement can be very handy sometimes.

---

### Post by mssever on 2008-04-23
Here's what I ended up with:
```
counter = 0
while True:
    try:
        foo.bar()
        break
    except TransientError:
        counter += 1
        if counter > 10:
            raise
```

---

### Post by Quikee on 2008-04-23
There is also an alternative way but I don't know if you will like it:

[PHP]
def foo():
    raise Exception, "eeeee"

def retryFunction():
    foos = [foo] * 10
    for eachFoo in foos:
        try:
            eachFoo()
        except Exception:
            pass
        else:
            return
    raise
retryFunction()
[/PHP]

---

### Post by mssever on 2008-04-23
> **Quikee said:**
> There is also an alternative way but I don't know if you will like it:

[php]
def foo():
    raise Exception, "eeeee"

def retryFunction():
    foos = [foo] * 10
    for eachFoo in foos:
        try:
            eachFoo()
        except Exception:
            pass
        else:
            return
    raise
retryFunction()
[/php]
That seems overly complicated to me.

I ended up modifying my solution slightly.
```
counter = 0
while True:
    try:
        foo.bar()
    except TransientError:
        counter += 1
        if counter > 10:
            raise
    else:
        break
```

---

### Post by Quikee on 2008-04-23
> **mssever said:**
> That seems overly complicated to me.

I ended up modifying my solution slightly.
```
counter = 0
while True:
    try:
        foo.bar()
    except TransientError:
        counter += 1
        if counter > 10:
            raise
    else:
        break
```

Yeah.. but it would still work if you would do it this way:

[PHP]def foo(i):
    print i
    raise Exception, "eeeee"

def try10():
    for i in xrange(10):
        try:
            return foo(i)
        except Exception:
            pass
    raise

try10()[/PHP]

I believe it is a neater but not so obvious solution.

---

### Post by Can+~ on 2008-04-23
> **Quikee said:**
> Yeah.. but it would still work if you would do it this way:

[PHP]def foo(i):
    print i
    raise Exception, "eeeee"

def try10():
    for i in xrange(10):
        try:
            return foo(i)
        except Exception:
            pass
    raise

try10()[/PHP]

I believe it is a neater but not so obvious solution.

But that would do 10 repetitions, even if it works. I know that you could add a break statement, but I prefer the one posted by mssever.

---

### Post by Quikee on 2008-04-23
> **Can+~ said:**
> But that would do 10 repetitions, even if it works. I know that you could add a break statement, but I prefer the one posted by mssever.

No .. if it works it will exit the function as there is a "**return** foo(i)" - foo function doesn't need to return anything for this to work. A break wouldn't work as you would break the for loop and would trigger raise which would raise the last exception occurred. ;) I agree that it might not be the most readable and obvious solution as it is a little bit evil.

---

