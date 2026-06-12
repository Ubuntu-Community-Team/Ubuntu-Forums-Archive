---
title: "Ignoring whitespace in a config file"
date: 2008-09-12
forum: Programming Talk
---

### Post by Xavieran on 2008-09-12
Hi guys,

I'm writing a function to parse a config file and have got stuck on one large problem.

I want to ignore any empty lines in the config file such as this:
```
GAMESTART
game=nethack
GAMEEND

GAMESTART
```

I have managed to ignore empty lines and lines with comments```

if '#' in opt[0] or opt[0] == '':pass
```
but if the line has spaces in it, it can't handle it.
Also, I can't just put in:
```
if '#' in opt[0] or opt[0] == '' or ' ' in opt[0]:pass
```
because some lines need spaces in them (to separate parts of an assigment)

Sorry if I haven't explained myself too well.

---

### Post by slavik on 2008-09-12
may I inquire as to what language you are using? if it's PPR, then look for the config module/library/class/code/symbols/configthingyorsomething

---

### Post by Xavieran on 2008-09-12
Sorry, I should have specified that.

Python.

---

### Post by slavik on 2008-09-12
I am sure Python has a config module.

---

### Post by ghostdog74 on 2008-09-12
you can ignore by testing for it
```

for line in open("file"):
    line=line.strip()
    if line: print line

```

---

### Post by ghostdog74 on 2008-09-12
> **slavik said:**
> I am sure Python has a config module.
configparser.

---

### Post by Xavieran on 2008-09-12
Genius! 
Thankyou,
I should have thought of that... :D

---

