---
title: "[python] Change a variable after X seconds"
date: 2009-10-18
forum: Programming Talk
---

### Post by Pyro.699 on 2009-10-18
Hey,

I need to do this in as little code as possible. I tried to use:

[php]
import threading, time

var = True
threading.Timer(exec, 1, "var = False")

while var:
    print "---"
    time.sleep(0.5)
print "End"
[/php]

but threading.Timer doesn't like that very much. I know that the first argument in threading.Timer is a function, but i would rather not make another function; that's how i have it set now.

Thanks
~Cody

---

### Post by Bachstelze on 2009-10-18
threading.Timer(exec, 1, exec("var = False"))

NOTE: I have't tried it, but it should work.

---

### Post by Pyro.699 on 2009-10-18
> **Bachstelze said:**
> threading.Timer(exec, 1, exec("var = False"))

NOTE: I have't tried it, but it should work.
That gives a ***SyntaxError: invalid syntax***

---

### Post by Bachstelze on 2009-10-18
Hmm, it doesn't work because exec is not a function. I think you'll have to write one.

---

### Post by kripkenstein on 2009-10-19
Yeah, exec isn't a function, and Python lambdas are a little limited. So you would need to write a function. But a generic one will work, like this:
```

def do_exec(cmd): exec(cmd)

t=threading.Timer(1, do_exec, ['global x; x = 7'])
t.start()

```
After 1 second, x will be set to 7.

With do_exec already defined, you can do later down in the same file things like
```

t=threading.Timer(3, do_exec, ['global x; x = 141'])
t.start()

```
and so forth.

---

