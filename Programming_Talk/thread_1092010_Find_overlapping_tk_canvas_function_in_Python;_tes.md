---
title: "Find_overlapping tk canvas function in Python; testing for tuple lengths"
date: 2009-03-09
forum: Programming Talk
---

### Post by kapok on 2009-03-09
in the if statement:
```
if enviornment.find_overlapping(enviornment.coords(x)[0],enviornment.coords(x)[1],enviornment.coords(x)[2],enviornment.coords(x)[3])[3]:
```
the find_overlapping function returns a tuple containing the identification numbers of all objects on top of the given point.
when i attempt to test for the length of this tuple(the number of objects overlapping at the given point) it returns the error:
```
 if enviornment.find_overlapping(enviornment.coords(x)[0],enviornment.coords(x)[1],enviornment.coords(x)[2],enviornment.coords(x)[3])[3]:
IndexError: tuple index out of range

```
whether or not that tuple index is out of range is what i'm trying to test for, except it gives me an error saying that it is instead of just returning false.

NOTE: the coordinate system i'm using is tested and working; it is within a for x in range()... loop that inputs the correct coordinates.

---

### Post by Can+~ on 2009-03-09
Two things:

There's a little trick in python to make your syntax shorter:

```
enviornment.find_overlapping(enviornment.coords(x)[0],enviornment.coords(x)[1],enviornment.coords(x)[2],enviornment.coords(x)[3])
```

Is the same as

```
enviornment.find_overlapping(*enviornment.coords(x))
```

(* unpacks the values of a sequence)

As for the problem, you're just assuming that there will be 4 colliding elements? If there's a collision of three objects, then the function will return a 3-tuple, but you try to access the 4th element (0, 1, 2, 3) and it doesn't exist, raising an error.

You can fix it, either:
-Checking the length of the returned array, using len() (Btw, len() still exists in py3?) and acting accordingly.
-using try: <stuff> except IndexError: <more stuff> and catch it, again, acting accordingly.

Seems that you don't know how errors are handled in python. When you do an if-else operation, it just tries to solve an arbitrary bool expression (look for boole's algebra). But in this if expression, how can you handle a glaring mistake? For example, imagine that this:

[PHP]if x/0 > 0:[/PHP]

returned true. That would make no sense at all, so what python does? Go with true or shout your mistake? If python would return true, then imagine how painful it would be to fix a huge app where suddenly, just because a 0 division occurred, everything is f... up. Instead python **raise**s an **exception**, so you can fix it, or, if you know that mistake will occur, then prevent it with try and except:

[PHP]y = 0

try:
    x = 1/y
except ZeroDivisionError:
    #oh "y" is 0, that means .... so it must be 1 again.
    y = 1[/PHP]

---

### Post by kapok on 2009-03-10
i must say, every time i need help, you jump to the occasion. 
thank you can+`.

the * thing is very useful.
but my try/except block is still backwards. 
i want it to only execute certain code if the error comes up.
but no matter whether i put the print function in the try section or the except section, it still prints only when there ARE four overlapping and that particular index position exists.
how do i get code to happen only if the error occurs?
```
try:
     enviornment.find_overlapping(*enviornment.coords(x))[3]
except IndexError:
     print ('there are fewer than 4 objects overlapping at this point, because the 4th position of the tuple does not exist')
```

and

```
try:
    enviornment.find_overlapping(*enviornment.coords(x))[3]
    print ('there are fewer than 4 objects overlapping at this point, because the 4th position of the tuple does not exist')
except IndexError:
    continue
```
do exactly the same thing; they both print while 4 objects are overlapping.

---

### Post by Can+~ on 2009-03-10
> **kapok said:**
> ```
try:
     enviornment.find_overlapping(*enviornment.coords(x))[3]
except IndexError:
     print ('there are fewer than 4 objects overlapping at this point, because the 4th position of the tuple does not exist')
```


That piece of code is correct, the message will be printed when the error exists.

My guess is that the problem is elsewhere.

---

### Post by kapok on 2009-03-11
yes; there was an error in my code.

when i changed from using enviornment.coords(x)[0],....... to *enviornment.getcoords(x) the error type changed to a TypeError, because instead of looking for am empty tuple position it didn't generate the tuple because the coordinates did not exist. 

thank you kindly.

---

