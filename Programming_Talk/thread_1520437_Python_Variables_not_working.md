---
title: "Python: Variables not working"
date: 2010-06-29
forum: Programming Talk
---

### Post by Tahakki on 2010-06-29
I have this (in simplified code):

```
class Main:
    def __init__(self):

        ind = 0

        def aFunction():
            ind += 1
```

This gives me the error:

local variable 'ind' referenced before assignment.

Anyone know why?

---

### Post by DanielWaterworth on 2010-06-29
You can't access variables outside of the current scope unless they are globals. You can find the current locals via the locals function.

---

### Post by Tahakki on 2010-06-29
Surely if I declare them in a parent all children must get those variables too?

What is the correct way to make these global? I understand the command, just not where and where not to put it.

---

### Post by Tony Flury on 2010-06-29
Daniel : Tahaki is using a class - you have other options other than glbals - in fact you should avoid using globals wherever you can.

Thaki  

by just using ind, then python thinks that ind is a local varibale in each function - and the ind in your "aFunction" is not the same as the ind in __init__

if you want ind to be an attribute of your class - then use 

[PHP]
self.ind
[/PHP]

In all places.

---

### Post by Tony Flury on 2010-06-29
> **Tahakki said:**
> Surely if I declare them in a parent all children must get those variables too?

What is the correct way to make these global? I understand the command, just not where and where not to put it.

You are not declaring them in a parent - you are declaring a local variable in the __init__ function - which ceases to exist when __init__ closes.

See my previous post for how todo class attributes - which is what I think you want to do - don't get into the habit of using globals.

---

### Post by Tahakki on 2010-06-29
Thanks very much, Tony, this seems to have solved my issue.

---

### Post by DanielWaterworth on 2010-06-29
To clear the matter up. You can read from the parent's scope, but you can't write to it unless it's global. So this works:

```
i = 0
def fn():
    print i
fn()
```To declare something as global, add global [var] to the beginning of the function declaration. However, from you're example it doesn't look like you want to declare it as global. Instead do something more like:

```
i = 0
def fn():
    return i + 1
i = fn(i)
```

edit: ah, not quick enough [=

---

### Post by Tahakki on 2010-06-29
Thanks Daniel, I understand variables better now. Probably still not as well as I should. :P

---

### Post by DanielWaterworth on 2010-06-29
> **Tony Flury said:**
> Daniel : Tahaki is using a class - you have other options other than glbals - in fact you should avoid using globals wherever you can.

I wouldn't suggest using globals either.

> **Tony Flury said:**
> if you want ind to be an attribute of your class - then use 

[PHP]
self.ind
[/PHP]In all places.

This will work with any readable class instance or container, (except tuple). If you prefer not to add new accessible attributes to you're class then you could make them private or make an instance of a nested class to hold the variables. Or you could just delete the attributes afterwards.

---

