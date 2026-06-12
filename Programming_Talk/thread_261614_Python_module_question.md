---
title: "Python module question"
date: 2006-09-20
forum: Programming Talk
---

### Post by ironfistchamp on 2006-09-20
Hey all

Just started programming in python. Damn its cool. Anyway I have a question. I am re-writing a game I wrote in C++. Simple text-based RPG. My question(s) is this. Should I split my program into modules? This would make it easier to change and view the code right? 

I tried putting it into a module but I use two Data Dictionaries throughout the program. I haven't been able to change the values of the data dictionaries outside of the main module. How exactly could I do that. 

Example

```

#Main module

Import module1

datadict = {"A": 1, "B": 2}

```
```


#module1

def myfunc():
 datadict["C"] = 3
```

Hope this makes sense. Basically the bit in module 1 throws up errors. Can I make it work?

Thanks 

Ironfistchamp

EDIT: Now seperated my modules.

---

### Post by thumper on 2006-09-20
There is a design pattern called "Parametise from above".  Basically you pass into the functions what they ned to change.

so
```
def myfunc(data):
   data['C'] = 3
```
Breaking up into modules doesn't necessarily make much difference in view and change other than enforcing some structure (which is a good thing).

A more concrete example is also better.  Split different files into different code blocks.

---

### Post by ironfistchamp on 2006-09-20
Hehe thanks. Didn't think to split it ](*,) .

Thanks again fo the answer I shall see what I can do now

Ironfistchamp

---

