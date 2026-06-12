---
title: "a simple question on python"
date: 2009-06-16
forum: Programming Talk
---

### Post by fr4nko on 2009-06-16
I've a small question for the python guys. I'm using often the following code pattern:
```

m = re.match(r'some (regexp) with captures', line)
if m:
    myval = m.group(1)
    # do something 
else:
    # do something else

```I don't like this code patterns because it is not compact and elegant as I would like. The problem is that I need to check if the matching is successful and the to retrieve the expression captured.

I'm sure someone will suggest me a more compact way to code patterns like that...

Francesco

---

### Post by Can+~ on 2009-06-16
> **fr4nko said:**
> I've a small question for the python guys. I'm using often the following code pattern:
```

m = re.match(r'some (regexp) with captures', line)
if m:
    myval = m.group(1)
    # do something 
else:
    # do something else

```I don't like this code patterns because it is not compact and elegant as I would like. The problem is that I need to check if the matching is successful and the to retrieve the expression captured.

I'm sure someone will suggest me a more compact way to code patterns like that...

Francesco

Compact not always is elegant, but if you insist, you could:

[PHP]m = re.match(r'some (regexp) with captures', line)
myval = m.group(1) if m else None[/PHP]

---

### Post by unutbu on 2009-06-16
You could also wrap the code pattern up in a def:
[PHP]
#!/usr/bin/env python
import re
def matches(pat,line):
    'Returns a tuple of all the match groups'
    m=re.match(pat,line)
    if m:
        return m.groups()
    else:
        return None

myval = matches(r'a(br.).*(br.)','abracadabra')
print(myval)
# ('bra', 'bra')[/PHP]
That way the rest of your code can stay nice and compact.

---

