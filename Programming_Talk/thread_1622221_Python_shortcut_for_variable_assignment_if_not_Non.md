---
title: "Python shortcut for variable assignment if not None"
date: 2010-11-15
forum: Programming Talk
---

### Post by MicahCarrick on 2010-11-15
Is there a pythonic shortcut to:

```
if some_value is not None:
    my_dict['key'] = some_value
```

---

### Post by MicahCarrick on 2010-11-15
I should add that my_dict['key'] is not defined before. In other words,

my_dict['key'] = some_value or None

will not work because the key 'key' shouldn't even exist in the dictionary if some_value is none.

---

### Post by Arndt on 2010-11-15
> **MicahCarrick said:**
> I should add that my_dict['key'] is not defined before. In other words,

my_dict['key'] = some_value or None

will not work because the key 'key' shouldn't even exist in the dictionary if some_value is none.

One question is whether you want an existing value to disappear in case some_value is None. Of course that's not what your code does, but sometimes it may be the proper thing to do.

(Not being a python expert, I dare not suggest that anything in particular is pythonic.)

---

### Post by ziekfiguur on 2010-11-15
I can't really think of a shortcut to do that. Maybe you can remove the `is not None' part depending on the type some_value. 
But what is the problem with using the if statement?

---

### Post by MicahCarrick on 2010-11-15
> But what is the problem with using the if statement? 

Nothing. My background is in C and PHP so I often overlook some of the beauty of python (like list comprehension). I have to make a conscious effort to take a second look at my code looking for pythonic ways to refactor bits.

I thought this may be one of those situations. Perhaps not.

Thanks everybody.

---

### Post by navneeth on 2010-11-15
> **MicahCarrick said:**
> Is there a pythonic shortcut to:

```
if some_value is not None:
    my_dict['key'] = some_value
```


> **MicahCarrick said:**
> I should add that my_dict['key'] is not defined before. In other words,

my_dict['key'] = some_value or None

will not work because the key 'key' shouldn't even exist in the dictionary if some_value is none.

Something like [http://docs.python.org/library/stdtypes.html#dict.setdefault](http://docs.python.org/library/stdtypes.html#dict.setdefault)?

---

### Post by CaptainMark on 2010-11-15
surely [if some_value is not None:] is the same as [if some_value:]

---

### Post by Arndt on 2010-11-15
> **CaptainMark said:**
> surely [if some_value is not None:] is the same as [if some_value:]

some_value = 0

---

### Post by nvteighen on 2010-11-16
I don't see the reason why you'd want a shortcut for that...

---

### Post by StephenF on 2010-11-16
If you want to assign a string in place of an empty string you can do code like:
```

dict[key] = input or default_string

``` This is a forced assignment unlike the code in your example which is why you need the if statement.

---

