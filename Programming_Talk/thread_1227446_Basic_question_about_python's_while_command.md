---
title: "Basic question about python's while command"
date: 2009-07-30
forum: Programming Talk
---

### Post by l951b951 on 2009-07-30
I'm using the Think Python online textbook to teach myself python.  In the Iteration chapter we're given some code examples to hash together to estimate a square root.  In this example, can you tell me what is being checked in the line that says while True: ?  I just can't get a handle on it in my head.

```
import math
epsilon = .000001


def square_root(a):
    x = .25*a
    while True:
        print x
        y = (x + a/x) / 2
        if abs(y-x) < epsilon:
            break
        x = y

square_root(9)
```

---

### Post by Dill on 2009-07-30
```
while True:
```

will always evaluate as *true*. If you were to run this program, for instance:

```
while True:
    print "hello, world!"
```

You'd see screen after screen of "hello, world!"'s flashing by you. Since the "loop continue condition" is always satisfied every time it's evaluated ("True" is always *true*), the loop will never exit by itself -- you'd have to call **break** or do something else to exit the loop "by force", as your example program does once the estimated square root has reached an "epsilon level" of precision.

Hope that helps.

Cheers,
Dill

---

### Post by l951b951 on 2009-07-30
Ok, so it's not checking to see if something is true; the while statement is being told that it IS true, so it runs indefinitely until the break command ends the loop because it is always true.  Am I understanding that right?  
So the while True: behaves the same as the following would (provided that variable did not, in fact, change)? 
```

unchanging_variable = 2
while unchanging_variable > 1:
    print 'Hello World'

```

---

### Post by Dill on 2009-07-30
It's still actually checking to see if "True" is true. Every while loop has to check it's given "loop continue condition" and see if it remains true. Since "True" is always true, it keeps iterating...

If you had loop like:

```
while count < 5
    count ++
```

it would keep checking to see if **count** was less than 5; that's the condition that must be true for the loop to continue iterating. So in our loop, it's still checking "True" everytime. And since "True" is still true... you get the picture.

I think you have it right, but the important thing to note is that the while loop **always checks** the condition we feed it to see if it remains true. The value "True" isn't telling the loop anything special, it just happens to always remain true, so the loop keeps iterating.

You're also right that the example loop you provided would also iterate for eternity. If you never change the "unchanging_variable", your loop keeps on going and going and going...

Cheers,
Dill

---

### Post by Can+~ on 2009-07-30
The thing is that while does not actually "compares", it's a dumb function that if it's true, it will go on, and if it's false it won't.

For example, in python you could easily type on the interactive shell:

[PHP]>>> 3 < 2
False[/PHP]

[PHP]>>> "Hello".lower() == "hello"
True[/PHP]

etc...

For example, let's take the following line

[PHP]
x = 3
y = -5
z = 2

if x > 2 and (y < 3 or z == 5)[/PHP]

The interpreter will go on the following order:

[PHP]if x > 2 and (True or False)[/PHP]
[PHP]if x > 2 and True[/PHP]
[PHP]if True and True[/PHP]
[PHP]if True[/PHP]

The thing is the comparison is independent of the statement being used, they only expect True/False.

And yes, you could do

[PHP]while 1 == 1:[/PHP]

and it would still work (probably the compiler recognizes this as redundant and replaces with True anyway)

---

### Post by l951b951 on 2009-07-30
> **Dill said:**
> 

I think you have it right, but the important thing to note is that the while loop **always checks** the condition we feed it to see if it remains true. The value "True" isn't telling the loop anything special, it just happens to always remain true, so the loop keeps iterating.


Ah, gotcha.  Thanks.

---

### Post by l951b951 on 2009-07-30
And thanks, Can +~.  That makes sense also.

---

### Post by jpkotta on 2009-07-31
> **Can+~ said:**
> 
For example, let's take the following line

[PHP]
x = 3
y = -5
z = 2

if x > 2 and (y < 3 or z == 5)[/PHP]

The interpreter will go on the following order:

[PHP]if x > 2 and (True or False)
if x > 2 and True
if True and True
if True[/PHP]

The thing is the comparison is independent of the statement being used, they only expect True/False.


Not quite.  **and** and **or** are short-circuit operators.  As soon as the interpreter knows what the value of the expression will be, it stops evaluating it.  It goes like this:

[PHP]x > 2 and (y < 3 or z == 5)
True and (y < 3 or z == 5)
True and (True or z == 5)
True and True
True[/PHP]

The **z == 5** is never evaluated, because anything **or**ed with True is True.  If z was undefined, it would not cause an error.

---

