---
title: "Function In Python to Detect Characters Regardless of Capitalization?"
date: 2009-06-11
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-06-11
Ey guys I was wondering if there was a built in function of some sort that allowed you to match a string of characters regardless if they are uppercase or lowercase in any combination. So if I had a string like "string" it would match with "STRING" or "stRInG" or "STRing" or any other combination. And if there isn't any such function, any ideas of how I would go about it in Python? Specifically, how would I go about manipulating acsii characters in Python? Thanks in advance!

---

### Post by monraaf on 2009-06-11
Something like:

[PHP]
"stRInG".lower()
[/PHP]

;)

---

### Post by StunnerAlpha on 2009-06-11
Uh... can I not use PHP code please? Thanks.

---

### Post by ghostdog74 on 2009-06-11
its not PHP code. It legit Python code. you are confusing it against something else...

---

### Post by StunnerAlpha on 2009-06-11
Ah ok cool thanks. Also I was wondering if there is any way to access the system time via python. I have looked at the documentation, but it seems convoluted, can someone give me a bit of sample code to retrieve the date from the system(unix based)? Thanks.

---

### Post by ghostdog74 on 2009-06-11
> **StunnerAlpha said:**
> Ah ok cool thanks. Also I was wondering if there is any way to access the system time via python. I have looked at the documentation, but it seems convoluted, can someone give me a bit of sample code to retrieve the date from the system(unix based)? Thanks.

well, if you want to use Python, then USE python. i am sure you know Python comes with its own time module.
eg
```

import time
print time.localtime(time.time())

```
please read the docs , especially the [library references](http://docs.python.org/library/) for details about various modules you can use with Python. Read from start to finish, and you won't need to ask here what library to use in future.

---

### Post by Greyed on 2009-06-11
Also unless you really need time use datetime.  Chances are what you want to do with time will be better served with datetime.

---

### Post by Greyed on 2009-06-12
> **StunnerAlpha said:**
> Uh... can I not use PHP code please? Thanks.

Meh, forgot to mention this in my last post.  Don't be confused by the "PHP Code" verbage over the code block.  UF has two different code block tags.  One is code and the other is php.  The code tag displays the contents inside the block with a fixed-width font.  The php tag also colorizes the code.  The colorization is not limited to PHP code.

```

# Python code with no color
for set in sets:
    if x in set:
        print("Yarrrr!")
        break
else:
    print("Shiver me timbers!")

```

[php]
# Most clearly Python in spite of what the line above says...
for set in sets:
    if x in set:
        print("Yarrrr!")
        break
else:
    print("Shiver me timbers!")
[/php]

---

