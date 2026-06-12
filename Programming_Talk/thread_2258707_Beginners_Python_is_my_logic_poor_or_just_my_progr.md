---
title: "Beginners Python: is my logic poor or just my programming skills?"
date: 2014-12-29
forum: Programming Talk
---

### Post by jim82 on 2014-12-29
Hello!

I'm working on learning python through code academy, and I recently passed one of their challenges... but it doesn't sit well with me. It took me forever to work through the logic, and though my solution works, I don't really feel it's the correct solution. The problem is to "*Write a function called digit_sum that takes a positive integer n as input and returns the sum of all that number's digits.For example: digit_sum(1234) should return 10 which is 1 + 2 + 3 + 4.(Assume that the number you are given will always be positive.)*"

My solution, with comments as I fear it may be too convoluted to understand:

```
def digit_sum(n):
    #mylist will hold ints to add
    mylist = []
    #x will count how many digits in n
    x = 0
    strnum = str(n)
    length = len(strnum)
    #divisor will create the proper multiple of ten to divide by
    divisor = 1
    #numsum will be final answer
    numsum = 0
    #generate the proper divisor by length
    zeros = length - 1
    while zeros > 0:
        divisor = divisor * 10
        zeros = zeros - 1
    #while loop counts digits in n
    while n > 1.0:
        #record initial number
        m = n 
        #round get the first number of sequence & round rest
        n = int(n / divisor) 
        #subtract the initial from the number taken to get what's left
        f = m - (n * divisor)  
        #decrease divisor to next tenths place
        divisor = divisor / 10
        #add to list
        mylist.append(n)
        #reset num to what was rounded off
        n = f
        #increment loop
        x = x + 1
    #loop list to add elements
    for num in mylist:
        numsum = numsum + num
    return numsum

```

I feel like the entire "divisor" bit is a messy workaround to the actual problem and I fear that there are likely instances other than just assuming a positive number for x that will cause the program to not work properly. I also feel that I have an excessive number of "counters", and that perhaps the entire structure of the program could be better. My concern is that I'm not sure if it's just because I'm a beginner, or if it's because I'm heading down a path or crappy logic that I need to correct now. 

Thanks for any help!

---

### Post by schragge on 2014-12-29
```

[COLOR=green]>>> [/COLOR]x=12345
[COLOR=green]>>> [/COLOR]eval('+'.join(n for n in str(x) if n.isdigit()))
[COLOR=green]15
>>> [/COLOR]x=-43.21
[COLOR=green]>>> [/COLOR]sum(int(n) for n in str(x) if n.isdigit())
[COLOR=green]10
>>> [/COLOR]

```

---

### Post by jim82 on 2014-12-29
Some of that is above my head, but if I were to translate it:

evaulate( by adding  looping characters in string x if they are digits)?

Essentially turning it into a string so you can cycle through each digit to add it?

Wow, I really missed the bullseye. Thanks for showing me your method!

---

### Post by schragge on 2014-12-29
Well, that's definitely not what beginner's book exercise would have in mind, but it shows nicely the power of python. It turns number into a string, and uses the fact that strings in python are iterable objects. As for the rest, see [List Comprehensions]("https://docs.python.org/2/tutorial/datastructures.html#list-comprehensions").

---

### Post by schragge on 2014-12-29
What your exercise *actually* was about is probably something like
```

def digit_sum(n):
        s=0
        while n > 0:
                s += n % 10
                n //= 10
        return s

```

---

