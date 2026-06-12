---
title: "[Python] string to variable conversion"
date: 2009-09-01
forum: Programming Talk
---

### Post by dodle on 2009-09-01
According to what I have found I need to use a dictionary to accomplish this, but I haven't been able to figure out how to do that.  I have a code that generates 10 strings and then puts them into a list.  What I want to do is convert each string to a variable and give it a value before it is appended to the list.  Any help is much appreciated.

[php]group = []
num = 0

while len(group) <= 10:
	name = "val%s" % num
	group.append(name)
	num += 1
	print group[/php]

Which prints out:
```
['val0']
['val0', 'val1']
['val0', 'val1', 'val2']
['val0', 'val1', 'val2', 'val3']
['val0', 'val1', 'val2', 'val3', 'val4']
['val0', 'val1', 'val2', 'val3', 'val4', 'val5']
['val0', 'val1', 'val2', 'val3', 'val4', 'val5', 'val6']
['val0', 'val1', 'val2', 'val3', 'val4', 'val5', 'val6', 'val7']
['val0', 'val1', 'val2', 'val3', 'val4', 'val5', 'val6', 'val7', 'val8']
['val0', 'val1', 'val2', 'val3', 'val4', 'val5', 'val6', 'val7', 'val8', 'val9']
['val0', 'val1', 'val2', 'val3', 'val4', 'val5', 'val6', 'val7', 'val8', 'val9', 'val10']
```

---

### Post by sloggerkhan on 2009-09-01
When you say 'convert to a variable' I think you are choosing a poor phrase.
If you want to be able to access items by key you could do the following (called a Dictionary):
```

>>> a = { "dog":1, "cat":2, "box":4 }
>>> a.get("cat")
2
>>> a["cat"]
2
>>> a["flower"] = 59
>>> a["flower"]
59

```

You should be able to use various types as keys, but if you have an integer named luxembold,  and you use it as a key, the key will be the value luxembold had, not 'the variable luxembold.' Likewise, duplicate keys are not allowed.

---

### Post by dodle on 2009-09-01
Okay, I think I know what I need to do now.  

[php]group = {}
num = 0

while len(group) <= 10:
	name = "val%s" % num
	group[name] = 100
	num += 1
print group["val9"][/php]

---

### Post by jpkotta on 2009-09-01
I have to wonder, is it worth it to use a string for the key?  Why wouldn't you just use num as the key?  If you have different types of keys, you can use a tuple instead of a string.
```

d = {}
d["descriptive name", num] = 1 # d[x,y] is shorthand for d[(x,y)]
d["different name", num] = 2

```

It just bugs me because there's a guy at work that overuses strings, so you have to do a bunch of string processing on things that really shouldn't need it.  I don't know your exact problem so maybe you're perfectly justified in using strings.

---

### Post by sloggerkhan on 2009-09-01
> **jpkotta said:**
> I have to wonder, is it worth it to use a string for the key?  Why wouldn't you just use num as the key?  If you have different types of keys, you can use a tuple instead of a string.
```

d = {}
d["descriptive name", num] = 1 # d[x,y] is shorthand for d[(x,y)]
d["different name", num] = 2

```

It just bugs me because there's a guy at work that overuses strings, so you have to do a bunch of string processing on things that really shouldn't need it.  I don't know your exact problem so maybe you're perfectly justified in using strings.

IMO if all the values are numbered, there's no reason he couldn't have stuck with an array and used index values.

---

### Post by G|N| on 2009-09-02
If you want to create a variable from a string dynamic you have to use the setattr() function.

```

setattr(object, name, value)
    This is the counterpart of getattr(). The arguments are an object, a string and an arbitrary value. The string may name an existing attribute or a new attribute. The function assigns the value to the attribute, provided the object allows it. For example, setattr(x, 'foobar', 123) is equivalent to x.foobar = 123.

```

So you have to put your loop in a class, pass the class, variable name and the value to the function and the attribute will be created.

---

