---
title: "GOTO in Python--can't figure out a workaround"
date: 2008-08-30
forum: Programming Talk
---

### Post by fiddler616 on 2008-08-30
Hey,
So (mainly to improve my programming skills, not really for the end-product), I'm making a little text-based Python adventure program. You know the type "Press 1 to go to the mountains, Press 2 to go down the hole" etc. Anyway, I'm using 4 8 6 and 2 (Numpad), and I want it to behave like this (written in a blend of BASIC and Python meant to be readable)
Label start
input var
if var = 2

 [indent]    go down, blah blah blah
if var = 4

[indent]    etc.
else:

 [indent]    print "You failure!"

  [indent]   GOTO start
This is impossible in Python--what do I do? I already tried Googling, and nothing very helpful came up.

---

### Post by mike_g on 2008-08-30
You can use code tags for pseudo code as in [ code ] [ / code ] without spaces. and it will retain the indentation. 

To avoid using GOTO you can use a while loop instead. In Basic-like pseudo code:
```
while(var <> 2 and var <> 4)
    input var
    if var = 2
        do something
    else if var = 4
        do something else
    else
       print "You failure!"
wend
```

Edit: the python syntax should be pretty similar:
[http://www.ehow.com/how_2091644_create-loop-python.html](http://www.ehow.com/how_2091644_create-loop-python.html)

---

### Post by Wybiral on 2008-08-30
BASIC is really bad for your brain...

```

asking = True
while asking:
    asking = False
    var = raw_input()
    if var == '2':
        pass
    if var == '4':
        pass
    else:
        print "You failure!"
        asking = True

```

You could also break out in the normal conditions (but chances are you'll be exiting more than redoing, so using a flag like this works).

---

### Post by fiddler616 on 2008-08-30
Thanks

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by fiddler616 on 2008-08-30
Wybiral: Didn't see yours until now: Brilliant! Thanks * 2

---

### Post by pycoder on 2009-01-04
```
num = None
while num not in ("2", "4", "6", "8"):
    num = raw_input()
```

---

