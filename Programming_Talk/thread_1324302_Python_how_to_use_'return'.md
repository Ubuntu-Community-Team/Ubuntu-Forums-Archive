---
title: "Python: how to use 'return'?"
date: 2009-11-12
forum: Programming Talk
---

### Post by jesuisbenjamin on 2009-11-12
Hello forum,

when creating a function i am not quite sure as how/why to use [FONT="Courier New"]return[/FONT]:
So far, my functions and programs have worked even though i did not end my function with [FONT="Courier New"]return[/FONT]. So what difference does this command make?

Secondly, local values (within a function) are not available outside the function. Now suppose i have several functions e.g. [FONT="Courier New"]F_1(), F_2(), F_3()[/FONT] and in each of those functions there is one activity which is common to all of them. To avoid making a huge program-script, i thought it would be sensible to create a common function e.g. [FONT="Courier New"]F_common()[/FONT] which would be called within each of my main functions.

However [FONT="Courier New"]F_common()[/FONT] needs to work with data which has been created in the main function, so for example, in [FONT="Courier New"]F_1()[/FONT] i call [FONT="Courier New"]F_common(data)[/FONT], and [FONT="Courier New"]F_common()[/FONT] does its job. But then when this is done, i want the freshly processed [FONT="Courier New"]data[/FONT] to return to [FONT="Courier New"]F_1()[/FONT] for further processes.

So as i thought so far (but perhaps i am mistaking) that [FONT="Courier New"]F_common()[/FONT] would have to go back through [FONT="Courier New"]F_1()[/FONT] after doing its job, it seemed logical that ending [FONT="Courier New"]F_common()[/FONT] with [FONT="Courier New"]return data[/FONT] would bring the processed [FONT="Courier New"]data[/FONT] back to [FONT="Courier New"]F_1()[/FONT]. 

But it didn't.

So why am i using return at all? What can i do to bring [FONT="Courier New"]data[/FONT] from [FONT="Courier New"]F_common()[/FONT] back into [FONT="Courier New"]F_1()[/FONT]?

Thanks.

---

### Post by benj1 on 2009-11-12
in simple use cases you don't need return
```

def foo():
    print "foo"

```
nothing would be gained, but its useful for returning a value, so you could do
```

def foo():
    return "foo"

#get a value and print
var = foo()
print var
#or even
print foo()

```

so to answer your question using 'return data' in F_common() should return data to F_1().

---

### Post by Can+~ on 2009-11-12
> **jesuisbenjamin said:**
> Hello forum,

when creating a function i am not quite sure as how/why to use [FONT="Courier New"]return[/FONT]:
So far, my functions and programs have worked even though i did not end my function with [FONT="Courier New"]return[/FONT]. So what difference does this command make?

...

So why am i using return at all? What can i do to bring [FONT="Courier New"]data[/FONT] from [FONT="Courier New"]F_common()[/FONT] back into [FONT="Courier New"]F_1()[/FONT]?

Thanks.

Own question answered.

Functions are like their mathematical counterpart, they receive arguments, work on that data, and return it:

```
x -> f(x) -> y
```

Return statement specifies what to give back to the caller of the function.

---

### Post by jesuisbenjamin on 2009-11-12
OK this sounds great, but in practice it doesn't work, or perhaps i don't understand you.

Here is an illustration:

```
def append_a(a):
    print 'when a arrives in append_a(), it looks', a
    a = a + ' and like that'
    print 'then it looks', a
    return a

def create_a():
    a = 'like this'
    print 'a in create_a() looks', a
    append_a(a)
    print 'after coming back to create_a(), a looks', a

create_a()
```

Will print:

```
a in create_a() looks like this
when a arrives in append_a(), it looks like this
then it looks like this and like that
after coming back to create_a(), a looks like this
```

Here it doesn't look like append_a() returned anything to create_a()...

---

### Post by Can+~ on 2009-11-12
y = f(x), otherwise, how would python know what to replace? In this case you must do:

x = f(x):

[PHP]def append_a(a):
    print 'when a arrives in append_a(), it looks', a
    a = a + ' and like that'
    print 'then it looks', a
    return a

def create_a():
    a = 'like this'
    print 'a in create_a() looks', a
    a = append_a(a) # here
    print 'after coming back to create_a(), a looks', a

create_a()[/PHP]

---

### Post by issih on 2009-11-12
One thing not yet mentioned is that usually (I don't know about in python specifically) you can have multiple return statements in a function.

e.g. you can return one specific thing from within a loop if a specific condition is matched, and return something else at the end of the function if the loop exits in some other way.

Sometimes this can make for very neat code flow..

---

### Post by jesuisbenjamin on 2009-11-12
> **Can+~ said:**
> 
x = f(x)


:-o but of course!!
it's so simply obvious, but i missed the point! :)

Thanks! :popcorn:

---

### Post by nvteighen on 2009-11-12
Welcome to the amazing world of programming interface design.

Each function has its interface, which is the way to connect to other functions. The interface is formed by an "input" (the parameters) and an "output" (the return value). Good design is the one which considers these interactions at best and creates suitable interfaces for this.

Sometimes you don't need an "input" the same way you sometimes don't need an "output". These "deadends" are not a bad thing of course, but if you don't ever rely on return values, you'll be soon crying for global variables and these, as you should know, are to be used with lot of care and wisdom.

---

### Post by jesuisbenjamin on 2009-11-12
Thanks for the tips! :)

---

