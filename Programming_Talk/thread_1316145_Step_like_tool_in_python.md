---
title: "Step like tool in python?"
date: 2009-11-05
forum: Programming Talk
---

### Post by briansykes on 2009-11-05
Hey, i searched around on google for this and couldn't find anything about it so i'm just wondering back when i used VB6 all those eons ago, i used a lovely little option in the for loop called Step like for example: For i = 0 To Len(str) Step 2, Now is there a python equivilent to that if so in VB6 you could use something along the lines of this to access the values:

array[i]
array[i + 1]

How would this be done in python? I'm trying to cycle through an array which is always dynamic, no idea if that helps or not.

If anyone is able to shed some light on this, it'd be very appreciated.

---

### Post by diesch on 2009-11-05
```
for i in xrange(0, len(str), 2):
   do_something
```

---

### Post by Can+~ on 2009-11-05
```
iterable[start:end:step]
```

Like:

[PHP]"Heelllloo  WWoorrlldd"[::2][/PHP]

---

### Post by smartbei on 2009-11-06
Check out [http://docs.python.org/tutorial/controlflow.html](http://docs.python.org/tutorial/controlflow.html), especially section 4.3.

---

### Post by briansykes on 2009-11-07
Hey thanks for all the replies guys, the thing is i receive information from a chat server and they give it to me like this User1#Online1#User2#Online2#User3#Online3 etc etc and the closest i've got was to use Can+~'s example here is a small example i just tried out in the python interpreter.

```
>>> t1 = "Hi1#There1#Hi2#There2".split("#")
>>> t1
['Hi1', 'There1', 'Hi2', 'There2']
>>> t1[1::2]
['There1', 'There2']
>>> t1[0::2]
['Hi1', 'Hi2']
>>> t1[0:1:2]
['Hi1']
>>> t1[1:2:2]
['There1']
>>> 

```

---

