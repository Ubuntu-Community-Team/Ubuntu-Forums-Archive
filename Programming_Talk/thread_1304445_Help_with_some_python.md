---
title: "Help with some python"
date: 2009-10-29
forum: Programming Talk
---

### Post by c2483 on 2009-10-29
```
endings = ['st', 'nd', 'rd'] + 17 * ['th'] + ['st', 'nd', 'rd'] + 7 * ['th'] + ['st']

day   = raw_input('Day (1-31): ')

ordinal = day + endings[day_number-1]
print ordinal
```

I read this in a book, not exactly but this is the relevant parts
I am having a problem understanding how endings works
Could someone explain please

---

### Post by Arndt on 2009-10-29
> **c2483 said:**
> ```
endings = ['st', 'nd', 'rd'] + 17 * ['th'] + ['st', 'nd', 'rd'] + 7 * ['th'] + ['st']

day   = raw_input('Day (1-31): ')

ordinal = day + endings[day_number-1]
print ordinal
```

I read this in a book, not exactly but this is the relevant parts
I am having a problem understanding how endings works
Could someone explain please

If you do the above interactively, you can see what the value of 'endings' is:

```
>>> endings = ['st', 'nd', 'rd'] + 17 * ['th'] + ['st', 'nd', 'rd'] + 7 * ['th'] + ['st']
>>> endings
['st', 'nd', 'rd', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'st', 'nd', 'rd', 'th', 'th', 'th', 'th', 'th', 'th', 'th', 'st']
>>> 
```

As you can see, the entries are the respective endings appropriate for each possible ordinal number.

---

### Post by delfick on 2009-10-29
which part don't you understand?

also, try this

[php]
def getEnding(num):
    
    #get the last number (for example, if num = 26, set num to 6)
    if len(str(num)) > 1:
        num = int(str(num)[-1])
        
    try:
        return {
            1 : 'st',
            2 : 'nd',
            3 : 'rd',
        }[num]
    except KeyError:
        return 'th'

while True:
    i = raw_input("Enter a day (1-31): ")
        
    try:
        num = int(i)
        if not 0 < num < 32:
            print "Needed a number between 1 and 31"
            num = None
            
    except ValueError:
        print "Needed a number, exiting now"
        num = None
    
    if num:
        print "You chose the %d%s" % (num, getEnding(num))
    else:
        #using exit is bad, but in such a small script, it's alright
        exit(1)
        
[/php]

:)

---

### Post by c2483 on 2009-10-29
ok thanks

---

### Post by nvteighen on 2009-10-29
This is a nice example to show how a general approach usually works in a much nicer way than a constrianed one. delfick's use of an anonymous dictionary + an Exception is very clever and makes the code completely reusable; also, it describes English's ordinal construction in a conceptually most precise fashion than the OP's... The OP isn't wrong, but that code needs more refinement, though the idea is well-leaded (using a data structure instead of a large amount of conditionals).

---

### Post by jesuisbenjamin on 2009-10-30
> **nvteighen said:**
> This is a nice example to show how a general approach usually works in a much nicer way than a constrianed one..

Yes it's a cool example thanks for sharing. :)

---

### Post by A_Fiachra on 2009-10-30
> **delfick said:**
> which part don't you understand?

also, try this

[php]
def getEnding(num):
    
    #get the last number (for example, if num = 26, set num to 6)
    if len(str(num)) > 1:
        num = int(str(num)[-1])
        
    try:
        return {
            1 : 'st',
            2 : 'nd',
            3 : 'rd',
        }[num]
    except KeyError:
        return 'th'

while True:
    i = raw_input("Enter a day (1-31): ")
        
    try:
        num = int(i)
        if not 0 < num < 32:
            print "Needed a number between 1 and 31"
            num = None
            
    except ValueError:
        print "Needed a number, exiting now"
        num = None
    
    if num:
        print "You chose the %d%s" % (num, getEnding(num))
    else:
        #using exit is bad, but in such a small script, it's alright
        exit(1)
        
[/php]:)


It's very cool.


But it is wrong for 11, 12, 13 ... the original code handles those cases :


```

def getEnding(num):

    endings = ['st', 'nd', 'rd'] + 17 * ['th'] + ['st', 'nd', 'rd'] + 7 * ['th'] + ['st']
    return endings[num-1]


```

I know it is only a toy example, but it illustrates the principle by which shortcuts will introduce bugs ... if in doubt, type it out!

:-)

---

### Post by mike_g on 2009-10-30
```
        
    try:
        return {
            1 : 'st',
            2 : 'nd',
            3 : 'rd',
        }[num]
    except KeyError:
        return 'th' 
```
I fail to see what is so cool about this. Having to use an exception to set a default value makes it look like something has gone wrong, when nothing has. Its just a very ugly switch statement. I thought the point of python was to make code readable? A simple if/else block would be much more appropriate imo.

---

### Post by delfick on 2009-10-30
> **nvteighen said:**
> This is a nice example to show how a general approach usually works in a much nicer way than a constrianed one. 

thankyou :)

> **jesuisbenjamin said:**
> Yes it's a cool example thanks for sharing. :)

:)

> **A_Fiachra said:**
> It's very cool.


But it is wrong for 11, 12, 13 ... the original code handles those cases :

hmmm, true

> **mike_g said:**
> I fail to see what is so cool about this. Having to use an exception to set a default value makes it look like something has gone wrong

that's certainly one way of looking at it.

another way of coding it is

[php]
ending = 'th'

try:
    ending = {
        1 : 'st',
        2 : 'nd',
        3 : 'rd',
    }[num]
except KeyError:
    #wasn't a 1, 2 or 3, so we'll use the default
    pass

return ending
[/php]

Which one is better becomes subjective.

In my case I was using the exception to indicate that it wasn't a 1, 2 or 3....

again, subjective :p :)

> Its just a very ugly switch statement.

As a technique, imho, it's less ugly than many if else statements 
especially when you have a heap of choices....

so anyway, the reason I don't use an array is you might want this functionality for numbers greater than 31. In such a case an array can never be big enough.

so my solution becomes :

[php]
def getEnding(num):
    """
        Numbers can be referred to as 1st, 2nd, 3rd, 4th, 5th, etc
        Generally if the number ends with a 1, it has a st
                                     with a 2, it has a nd
                                     with a 3, it has a rd
                                     Otherwise it has a th
        
        The only exception is when a number ends in 11, 12 or 13 in which case its a th
    """
    
    #first we make sure num is a number
    try:
        num = int(num)
        if num < 1:
            raise ValueError
    except ValueError:
        #ValueError risen if number isn't integer or if it's less than 1
        raise ValueError, "Need an integer greater than 0"
    
    parts = str(num)
    
    #We'll handle the special case of 11, 12 and 13 first 
    if len(parts) > 1:
        lastTwo = parts[-2:]
        if lastTwo in ('11', '12', '13'):
            return 'th'
    
    #number doesn't end with 11, 12 or 13, follow normal rules now
    lastNum = parts[-1]
    ending = 'th'

    try:
        ending = {
            '1' : 'st',
            '2' : 'nd',
            '3' : 'rd',
        }[lastNum]
    except KeyError:
        #wasn't a 1, 2 or 3, so we'll use the default
        pass
    
    return ending

if __name__ == '__main__':
    while True:
        try:
            i = raw_input("Enter a number: ")
        except EOFError:
            print "\nExiting now..."
            break
            
        try:
            print "You chose the %s %s" % (i, getEnding(i))
        except ValueError, v:
            print v
            break
[/php]

and for the purposes of completion, the anonymous dict can be replaced with an array :

[php]
lastNum = parts[-1]
ending = 'th'

try:
    ending = ['', 'st', 'nd', 'rd'][int(lastNum)]
except IndexError:
    #wasn't a 1, 2 or 3, so we'll use the default
    pass

return ending
[/php]

or an if-else :)

[php]
    lastNum = parts[-1]
    
    if   lastNum == '1':
        ending = 'st'
        
    elif lastNum == '2':
        ending = 'nd'
        
    elif lastNum == '3':
        ending = 'rd'
        
    else:
        ending = 'th'

    return ending
[/php]

if-else has too much mundane repetition for my liking, even with just four choices.........

:D

---

### Post by diesch on 2009-10-30
```
if len(str(num)) > 1: 
        num = int(str(num)[-1]) 
```
could be replaced by

```
num = num%10
```

---

### Post by diesch on 2009-10-30
> **mike_g said:**
> ```
        
    try:
        return {
            1 : 'st',
            2 : 'nd',
            3 : 'rd',
        }[num]
    except KeyError:
        return 'th' 
```I fail to see what is so cool about this. Having to use an exception to set a default value makes it look like something has gone wrong, when nothing has. Its just a very ugly switch statement. I thought the point of python was to make code readable? A simple if/else block would be much more appropriate imo.


I'd prefer

```
return {
           1 : 'st',
           2 : 'nd',
           3 : 'rd',
        }.get(num, 'th')

```

---

### Post by benj1 on 2009-10-30
> **diesch said:**
> I'd prefer

```
return {
           1 : 'st',
           2 : 'nd',
           3 : 'rd',
        }.get(num, 'th')

```

```
return {
           1 : 'st',
           2 : 'nd',
           3 : 'rd',
        }.get(num > 20 and num%10 or num, 'th')

```
for the 21st for example?

i like the try except block but exceptions are quite expensive, so its probably not a good idea to use it for the majority of cases, but yes i know it probably wouldnt matter in this instance

---

### Post by Can+~ on 2009-10-30
> **mike_g said:**
> ```
        
    try:
        return {
            1 : 'st',
            2 : 'nd',
            3 : 'rd',
        }[num]
    except KeyError:
        return 'th' 
```
I fail to see what is so cool about this. Having to use an exception to set a default value makes it look like something has gone wrong, when nothing has. Its just a very ugly switch statement. I thought the point of python was to make code readable? A simple if/else block would be much more appropriate imo.

I also don't like exceptions being used on like that, but on that case, a simple test would satisfy both parties (and it's more efficient, apparently):

[PHP]if num in mydict:
    # do stuff.[/PHP]

And other alternatives include using defaultdict on the collections module.

Also, this could be done with a modulo mapping, because the last number represents the termination (as someone posted above).

> I thought the point of python was to make code readable?

And it is more readable. It is the programmer who decides what's readable, and what's not. The decision on this case of using the except statement was purely out of the programmer, and not a language choice (you have multiple alternatives).

---

### Post by delfick on 2009-10-30
Yes, using mod is much better than what I was doing :)

[php]
from cProfile import Profile
import random

def profile(f):
    def wrapper(*args, **kwargs):
        profiler = Profile()
        try:
            profiler.runcall(f, *args, **kwargs)
        finally:
            print profiler.print_stats()
    return wrapper

@profile
def usingStr(numbers):
    for num in numbers:
        lastTwo = str(num)[-2]

@profile
def usingMod(numbers):
    for num in numbers:
        lastTwo = int(num % 100)

if __name__ == '__main__':
    numbers = [random.random()*(100000/random.random()) for i in range(100000)]
    usingStr(numbers)
    usingMod(numbers)
    
"""
RESULTS IN :
    UsingStr takes 0.224 CPU seconds
    usingMod takes 0.037 CPU seconds

Even with 100 numbers, there's still quite a difference.....
"""
[/php]

As for exceptions vs using dict.get....

dict.get wins :)

[php]
from cProfile import Profile
import random

def profile(f):
    def wrapper(*args, **kwargs):
        profiler = Profile()
        try:
            profiler.runcall(f, *args, **kwargs)
        finally:
            print profiler.print_stats()
    return wrapper

@profile
def usingException(numbers):
    for num in numbers:
        try:
            ending = {
                1 : 'st',
                2 : 'nd',
                3 : 'rd',
            }[num]
        except KeyError:
            ending = 'th'

@profile
def usingGet(numbers):
    for num in numbers:
        ending = {
            1 : 'st',
            2 : 'nd',
            3 : 'rd',
        }.get(num, 'th')

if __name__ == '__main__':
    numbers = [int(random.random()*10) for i in range(1000000)]
    usingException(numbers)
    usingGet(numbers)
    
"""
RESULTS IN :
    usingException takes 1.358 CPU seconds
    usingGet       takes 0.732 CPU seconds
"""
[/php]


:)

---

