---
title: "how do I type Greek letters in Python?"
date: 2013-07-08
forum: Programming Talk
---

### Post by AirbornEagle on 2013-07-08
I'm a beginner of programming. I should type a math formula but I can't find the way to type Greek letters such as alpha, beta and so on. I've already looked for info on the Internet but I always read stuff about matplotlib and plots that I think I don't need for my simple problem. If I select the font I don't find anything for Greek symbols. Hope someone could help me, thank you!

I'm using Python 2.7.5

---

### Post by Bachstelze on 2013-07-08
What *exactly* do you mean by "type" here?

---

### Post by AirbornEagle on 2013-07-08
I want to write sin(alpha) - can't find the Greek alpha symbol

---

### Post by Vaphell on 2013-07-08
but do you need to print that out as a part of its output or do you want to be able to type that when the program prompts for user input?

---

### Post by AirbornEagle on 2013-07-08
> **Vaphell said:**
> but do you need to print that out as a part of its output or do you want to be able to type that when the program prompts for user input?

yes, I want to type stg like that:

alpha = input("Enter alpha value: ")
beta = ...
x = sin(alpha) + cos(beta)
print x

---

### Post by CptPicard on 2013-07-08
While it is possible to use Unicode either in Python source or maybe even in the shell, doing so is just asking for encoding-related troubles. Why not just call it "alpha" like everyone else would?

---

### Post by AirbornEagle on 2013-07-08
I know but it's an excercise from a book and I should type it that way 

I'll try to get info about Unicode, thank you CptPicard :)

---

### Post by alan9800 on 2013-07-08
the following code shows all the greek letters```
for greek_code in range(0x3b1,0x3ca):
    greek_char = unichr(greek_code).encode('utf-8')
    print hex(greek_code), greek_char
```you may find more infos about how to use unicode in your python scripts here:
[http://docs.python.org/2/howto/unicode.html](http://docs.python.org/2/howto/unicode.html)

---

### Post by Vaphell on 2013-07-08
strings are one thing but apparently python 2.x doesn't allow for non-ascii chars in variable names at all. Python 3.x does but only accepts ones that are letters (eg **µ** is ok but **&#8730;** is not)

---

### Post by SledgeHammer_999 on 2013-07-08
Go to your keyboard settings and add a new layout. Choose greek. Then choose a key combination that switches between the layouts or click on the relevant tray icon that appears.

---

### Post by CptPicard on 2013-07-08
> **AirbornEagle said:**
> I know but it's an excercise from a book and I should type it that way 


What kind of book? Why? What difference does it make?

---

### Post by AirbornEagle on 2013-07-08
> **CptPicard said:**
> What kind of book? Why? What difference does it make?

the book is "Python programming: an introduction to computer science - John Zelle"

It doesn't really make any difference, it's just matter of learning to type those characters since I came across them :)

---

### Post by AirbornEagle on 2013-07-08
> **alan9800 said:**
> the following code shows all the greek letters```
for greek_code in range(0x3b1,0x3ca):
    greek_char = unichr(greek_code).encode('utf-8')
    print hex(greek_code), greek_char
```you may find more infos about how to use unicode in your python scripts here:
[http://docs.python.org/2/howto/unicode.html](http://docs.python.org/2/howto/unicode.html)

thanks ;)

---

### Post by nvteighen on 2013-07-09
This works flawlessly for me. 

```

# -*- coding: utf-8 -*-

alpha = raw_input("Type &#945;:")
if alpha == "&#945;":
    print "&#7940;&#961;&#953;&#963;&#964;&#945;."
else:
    print "&#964;&#959;&#8166;&#964;&#959; &#959;&#8016; &#7952;&#963;&#964;&#8054; &#964;&#8056; &#7940;&#955;&#966;&#945;."

```

Translating the print statements is left as an exercise to the reader.

---

### Post by alan9800 on 2013-07-09
> **nvteighen said:**
> This works flawlessly for me. 

```

# -*- coding: utf-8 -*-

alpha = raw_input("Type &#945;:")
if alpha == "&#945;":
    print "&#7940;&#961;&#953;&#963;&#964;&#945;."
else:
    print "&#964;&#959;&#8166;&#964;&#959; &#959;&#8016; &#7952;&#963;&#964;&#8054; &#964;&#8056; &#7940;&#955;&#966;&#945;."

```

Translating the print statements is left as an exercise to the reader.Perhaps I've forgot something of what I studied at the high school, but shouldn't the first string be "&#7940;&#961;&#953;&#963;&#964;&#959;&#957;" instead of "&#7940;&#961;&#953;&#963;&#964;&#945;"?

---

### Post by nvteighen on 2013-07-09
> **alan9800 said:**
> Perhaps I've forgot something of what I studied at the high school, but shouldn't the first string be "&#7940;&#961;&#953;&#963;&#964;&#959;&#957;" instead of "&#7940;&#961;&#953;&#963;&#964;&#945;"?

It's a synonym :)

---

