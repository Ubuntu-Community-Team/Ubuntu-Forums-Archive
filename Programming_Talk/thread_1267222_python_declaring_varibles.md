---
title: "python declaring varibles"
date: 2009-09-15
forum: Programming Talk
---

### Post by chelom on 2009-09-15
hey everyone, im new to this forum. i come here because i have a dude about how u declare variables in python. 
for example i want to write the numbers from 1 to 10, and asing a varible number1=1 number2=2. and im wondering if theres a way to change the # in numbers# while asigning a varible. gonna put a fast example with a code.
```

>>>counter=1
>>>for k in range(1,11):
       number(counter)=k
       counter=counter+1

```
well ofc that not the way not even sure if theirs a way but i think u can get the idea of what im wondering and thanxs for the help.

---

### Post by hofsmo on 2009-09-15
A list will probably do the job
[PHP]>>>counter=1
>>>for k in range(1,11):
       number[counter]=k
       counter=counter+1
[/PHP]

---

### Post by nvteighen on 2009-09-15
Heck, that sounds almost like you wanted Lisp's metaprogramming... :P

There is a way to do such a thing, by using **eval**... though, it's also true that unless there's a good reason to do it in that other way, the list is the best.

---

### Post by unutbu on 2009-09-15
chelom, here is one way to assign values to variables called number1,...,number10:
[PHP]
#!/usr/bin/env python
import sys
main=sys.modules['__main__']
for k in range(1,11):
    setattr(main,'number%s'%k,k)
print(number5)[/PHP]

Although it is cute to know about, it is unnecessary. Using a dict, as hofsmo suggested, is a much better idea:
[PHP]
number={}
for k in range(1,11):
    number[k]=k
print(number[5])
[/PHP]

---

### Post by Can+~ on 2009-09-15
You could, but it wouldn't make a lot of sense. How could you ensure those variables exist later, it may crash with other names, etc.

But the closest thing you can get is a list as someone else pointed out.

python 2.6:
```
alist = range(0, 11)
```

python 3.x:
```
alist = [i for i in range(0, 11)]
```

Or, if you want particular names, a dictionary:

Python 3.x
```
adict = dict(("variable%d" % i, i) for i in range(0, 11))
```

Having everything packed inside another data structure, makes it easier to juggle the values later. If you're creating variables with name1, name2, name3... nameN; it makes more sense to have a specific data structure to hold them and be able to perform operations with the whole list instead of having to request each element individually.

---

### Post by chelom on 2009-09-16
well  thaxs a lot. pretty sure i wouldnt do it for now. the list method doesnt know its gonna work for my porpuses, i guess i will write them all down. XD

---

### Post by nvteighen on 2009-09-17
> **chelom said:**
> well  thaxs a lot. pretty sure i wouldnt do it for now. the list method doesnt know its gonna work for my porpuses, i guess i will write them all down. XD

Hm... An important detail in programming is abstraction. And well-designed data structures are vital to it... It's much more senseful to use a "variable package" and pass that around than lots of variables... Specially because if you just use non-combined variables, it will make you call functions much harder than by using lists or other more complex structures.

It's all about abstraction and also about practicity.

---

