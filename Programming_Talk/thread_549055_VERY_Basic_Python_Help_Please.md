---
title: "*VERY* Basic Python Help Please"
date: 2007-09-12
forum: Programming Talk
---

### Post by Catsworth on 2007-09-12
Hi Guys,

I've got a really noddy Python question I'm afraid, but I'm stuck and banging my head against the desk isn't helping :(

Here's my code:

```

def sayHello(name):
    """Say hello to me.
    
    Please."""
    print "Hello " + name

if __name__ == "__main__":
   sayHello("Catsworth")

```

The file this is in is called 'hello.py'.

Now, if I type the following into a command prompt:

```
python hello.py
```

I get the output that I am expecting:

```
Hello Catsworth
```

But, what I actually want to do is supply an argument when I call the program, in the format:

```
python hello.py("Catsworth")
```

So, I've revised the code so that it reads:

```
def sayHello(name):
    """Say hello to me.
    
    Please."""
    print "Hello " + name

if __name__ == "__main__":
   sayHello(who)
```

But now when I try to call:

```
python hello.py("Catsworth")
```

I get the following error:

```
bash: syntax error near unexpected token `('
```

Please could someone point me at what I'm doing wrong here.  Eventually the argument needs to be a file name, or the path to a file, but if I can't even get a simple string right.....

---

### Post by Catsworth on 2007-09-12
Ok, so I now know that the command line should be:

```
python hello.py "robert"
```

But It still doesn't work:

```
Traceback (most recent call last):
  File "hello.py", line 9, in ?
    sayHello(name)
NameError: name 'name' is not defined
```

---

### Post by bashologist on 2007-09-12
Try this code.
```
#!/usr/bin/env python
import sys
print sys.argv[1:]
```
So, you need to add the import and replace name with sys.argv[1].

---

### Post by Catsworth on 2007-09-12
Got it now:

```

import sys

def sayHello():
    """Say hello to me.
    
    Please."""
    name = str(sys.argv[1])
    print "Hello " + name

if __name__ == "__main__":
sayHello()
```

Thanks :)

---

