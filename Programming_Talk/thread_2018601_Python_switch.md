---
title: "Python switch"
date: 2012-07-06
forum: Programming Talk
---

### Post by bobman321123 on 2012-07-06
How would I convert the following block from C++ into Python?
```

cin >> input;
switch(input)
{
case 'testing': anotherVariable=4;
break;
case 'etc': thisVariable=87;
break;
default: break;
}

```

---

### Post by Barrucadu on 2012-07-06
[http://docs.python.org/faq/design.html#why-isn-t-there-a-switch-or-case-statement-in-python](http://docs.python.org/faq/design.html#why-isn-t-there-a-switch-or-case-statement-in-python)

---

### Post by MadCow108 on 2012-07-06
any switch statement can be converted to if..elif..else

```

if input == 'testing':
   pass
elif input == 'etc':
  pass
else:
  pass

```

but you don't have a compiler to optimize that to a jump table, you would have to do that yourself
luckily its easy with python dictionaries.

also note that input is a builtin function in python3, its better not to shadow it.

---

### Post by bobman321123 on 2012-07-06
> **MadCow108 said:**
> any switch statement can be converted to if..elif..else

```

if input == 'testing':
   pass
elif input == 'etc':
  pass
else:
  pass

```but you don't have a compiler to optimize that to a jump table, you would have to do that yourself
luckily its easy with python dictionaries.

also note that input is a builtin function in python3, its better not to shadow it.

Is there any way you could do the above with a dict? I can't figure out how to set a variable value in a dict.

---

### Post by MadCow108 on 2012-07-06
just return the value you want in your function (or lambda) and assign it to what you want:

```

jumptable = dict(testing=lambda: 187)
thisvariable = jumptable.get(input, lambda : 'default')()
```

edit:
just saw you assign to different variables in switch (which seems like a bad design, it may leave stuff uninitialized, its better to branch of to different functional paths)
it is of course possible, but it probably gets ugly
do you really need a jumptable for this?
the python way favors readability over performance

one (ugly) way I can think of right now would look like this:
```
jumptable = dict(testing=lambda: ('var1',187), etc=lambda: ('var2','bla'))
res = jumptable["testing"]()
locals()[res[0]] = res[1]
```

---

