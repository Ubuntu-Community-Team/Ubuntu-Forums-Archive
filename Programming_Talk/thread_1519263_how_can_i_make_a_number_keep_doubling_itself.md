---
title: "how can i make a number keep doubling itself?"
date: 2010-06-27
forum: Programming Talk
---

### Post by unter on 2010-06-27
i am playing around in y terminal with little counting programs .. i decided to make something that shows a number that keep doubling itself
egsample: (i am doing this in ruby)

puts 1
puts 1 + 1
puts 2 + 2

but obviosuly this is silly because i dont want to type all the statements. i want the program 
to keep doubling a variable and outputting it

i have desire to see how big number in my terminal can get before program breaks down or computer explodes/whatever 

can someone assist me? I do not care what language ..

(I am brand new to programming, obviously? :D )

---

### Post by trent.josephsen on 2010-06-27
What you want is a variable to hold your value and a loop.

```
# Python code
n = 1
while n < 1000000:
    print n
    n = n + n
```
An interesting feature of Python is that this loop will never cause n to overflow, because Python's integers can be arbitrarily long.  Other languages will mostly not act like this.  To find out what Python does instead, replace "n < 1000000" in the above code with "True".  You may want to use Ctrl-C to stop the program after a while.

---

### Post by unter on 2010-06-27
hehe thanks :)

that while < 1000000 stopped at 524288 so i put it into and infinite loops to keep doubling ...

```
# Python code
n = 1
blah = 0
while n != blah:
    print n
    n = n + n
```

it has been going for about 5 minutes now. 

what will happen if i let this keep going? even though it will never over flow, will it eventually use up all my ram?

---

### Post by shadylookin on 2010-06-28
you'll never use up all of your ram since there's only one variable. it's an infinite loop that will just continue on forever until you stop it.

---

### Post by endotherm on 2010-06-28
> **unter said:**
> hehe thanks :)

that while < 1000000 stopped at 524288 so i put it into and infinite loops to keep doubling ...

```
# Python code
n = 1
blah = 0
while n != blah:
    print n
    n = n + n
```it has been going for about 5 minutes now. 

what will happen if i let this keep going? even though it will never over flow, will it eventually use up all my ram?

in most languages this will eventually crash when you exceed the max range of n, but in python the size of a numeric type is platform dependent. here is mine:
```

$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.maxsize
9223372036854775807
>>> 

```[http://docs.python.org/library/stdtypes.html](http://docs.python.org/library/stdtypes.html)

---

### Post by xaegis on 2010-06-28
> **endotherm said:**
> in most languages this will eventually crash when you exceed the max range of n, but in python the size of a numeric type is platform dependent. here is mine:
```

$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.maxsize
9223372036854775807
>>> 

```[http://docs.python.org/library/stdtypes.html](http://docs.python.org/library/stdtypes.html)

WoW! :shock: 
Your computer must be a beast!!!

---

### Post by unter on 2010-06-28
> **endotherm said:**
> in most languages this will eventually crash when you exceed the max range of n, but in python the size of a numeric type is platform dependent. here is mine:
```

$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.maxsize
9223372036854775807
>>> 

```[http://docs.python.org/library/stdtypes.html](http://docs.python.org/library/stdtypes.html)

hello this has offed me now.

as i test my max and it is smaller than yours in fact.

though when i run this it explodes bigger than python what said max:

```

# Python code
n = 1
blah = 0
while n != blah:
    print n
    print " \n \n "
    n = n + n
```

```
2215827865120445285436604169234485268788427414982608644747394113713414456
1892813049929861940386240938153843936177983478463509458982123519596320846
3952302131918515390224376302054924727951630612741446375218384182036827169
1660401046407456843466086176161485977628013706077372678144
 
 
 
4431655730240890570873208338468970537576854829965217289494788227426828912
3785626099859723880772481876307687872355966956927018917964247039192641692
7904604263837030780448752604109849455903261225482892750436768364073654338
3320802092814913686932172352322971955256027412154745356288
```

do i no understand sys.maxsize?

---

### Post by unter on 2010-06-28
> **xaegis said:**
> WoW! :shock: 
Your computer must be a beast!!!

hehe think he just with reason to show off his max :D

---

### Post by DanielWaterworth on 2010-06-28
> sys.maxsize:
The largest positive integer supported by the platform&#8217;s Py_ssize_t  type, and thus the maximum size lists, strings, dicts, and many other  containers can have.You are using longs though, and they can get much bigger. My computer is happy to do 10**10000.

edit: In fact it'll cope with math.log(2**100000000)/math.log(2) where 2**100000000 is about a 12MB number!

---

### Post by simeon87 on 2010-06-28
> **shadylookin said:**
> you'll never use up all of your ram since there's only one variable. it's an infinite loop that will just continue on forever until you stop it.

For all practical purposes, it's an infinite loop. But given that a computer has finite memory so even if the amount of memory reserved for that number were allowed to grow, it would stop or overflow at some point. If the amount of memory for a number is finite, it'll stop or overflow earlier. Logically, no computer can keep an arbitrarily increasing number in memory until the end of time :popcorn:

---

### Post by unter on 2010-06-28
> **simeon87 said:**
> For all practical purposes, it's an infinite loop. But given that a computer has finite memory so even if the amount of memory reserved for that number were allowed to grow, it would stop or overflow at some point. If the amount of memory for a number is finite, it'll stop or overflow earlier. Logically, no computer can keep an arbitrarily increasing number in memory until the end of time :popcorn:

could limit be worked out with followng information?

a) how many bits are used by a digit
b) how many bits are in memory


?

---

### Post by simeon87 on 2010-06-28
> **unter said:**
> could limit be worked out with followng information?

a) how many bits are used by a digit
b) how many bits are in memory


?

In theory, yes, if you also know the way a number is represented. Then, by using all of the available bits, you could determine the maximum number that could practically be stored by the computer at hand.

---

### Post by DanielWaterworth on 2010-06-28
The lower bound on the memory used to store i is log2 i. At step n, the program outputs 2^n, so the memory being used is log2 2^n == n log2 2 == n ie. The maximum number of iterations is the size in bits of the available memory.

---

### Post by unter on 2010-06-28
> **DanielWaterworth said:**
> The lower bound on the memory used to store i is log2 i. At step n, the program outputs 2^n, so the memory being used is log2 2^n == n log2 2 == n ie. The maximum number of iterations is the size in bits of the available memory.

unfortunately i not understand any mathematical notation as you have formulated.
can you say above in easy term? like " 1 + ten thousand zero"?

:)

---

### Post by simeon87 on 2010-06-28
However, no computer will ever fill its entire memory with one number.

Even if you use a counter in a loop that would not overflow within our lifetime, I still think it's bad programming style to do so. It's better to use while True and then break when needed.

---

### Post by DanielWaterworth on 2010-06-28
I haven't looked at the python 'long type' implementation, but if it's written to process any size integer, I think it would be able to use lots of memory to store just one integer.

It's difficult to say how big the largest number that the program would print out is before the computer crashed, or how long it would take to get there. All I can say is that I wouldn't sit around waiting for it =P

If each iteration uses an extra bit on average. Then for each MB you'd have to go through 8*1024^2 = 8388608 iterations. I don't know how the console reacts, but I think it has an upper bound on size and hence memory use.

If you didn't have to print out the number in decimal, then you could store the number with runtime-coding in binary and the program could go on exponentially longer.

I would always recommend while True: rather than a large counter variable if you intend to create an infinite loop.

---

### Post by lisati on 2010-06-28
> **unter said:**
> unfortunately i not understand any mathematical notation as you have formulated.
can you say above in easy term? like " 1 + ten thousand zero"?

:)

"log" is short for "[logarithm]("http://en.wikipedia.org/wiki/Logarithm")"
log2 refers to logarithms based on [powers]("http://en.wikipedia.org/wiki/Power_%28mathematics%29") of two
2^n means "2 to the power of n"
10^n is a 1 followed by 'n' zeros, so 10^2=10*10=100.

Hope this helps.

---

### Post by unter on 2010-06-28
> **lisati said:**
> "log" is short for "[logarithm]("http://en.wikipedia.org/wiki/Logarithm")"
log2 refers to logarithms based on [powers]("http://en.wikipedia.org/wiki/Power_%28mathematics%29") of two
2^n means "2 to the power of n"
10^n is a 1 followed by 'n' zeros, so 10^2=10*10=100.

Hope this helps.

thanks!

---

