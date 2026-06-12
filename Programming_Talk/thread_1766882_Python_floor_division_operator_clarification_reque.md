---
title: "Python: floor division operator clarification request"
date: 2011-05-24
forum: Programming Talk
---

### Post by 770aky on 2011-05-24
Hi all, 

I'm a newbie learning python. I've been stuck with an issue for the past week that I can't seem to get around. I will be very grateful if anyone who can point me in the right direction.

**Short Version:**
I know that the operator "//" in python is suppose to give the floor of the quotient.  It all looks great for something like this:

```

>>> 23//2
11

```

But as soon as I use a number like .1 or .01 for the denominator, it gives me a floor always one less than what I am expecting.  (I've tried specifying both values as floats--still the same result.)

```

>>> 20//.1
199.0
>>> 20/.1
200.0
>>> 20//.01
1999.0
>>> 20/.01
2000.0

```

There seems to be some fundamental concept about the floor operator that I might have misunderstood.  I expected that the floor operator would give me a 'multiplier'-- Eg. 23//10 will be 2--without all the values after the decimal point.  Can someone please clarify what's going on?   Is there a way around this (see below for more details)?

Thank you for your help!

** The Real Issue (Long Version) **

I've been trying to write a small program, change.py, that calculates the most efficient change to give back. The program will ask for how much money you owe and gave.  Based on that, it will calculate the change to give back in bills/coins.  Here's what a 'good' run looks like so far (owe and gave are the only inputs):

```

How much you owe: 23.34
How much you gave: 33
Thank you, your change will be: $9.66
You will be given:
1x $5
4x $1
2x $0.25
1x $0.1
1x $0.05
1x $0.01

```

But other times it doesn't do such a good job at calculating the change:

```

How much you owe: .24
How much you gave: .94
Thank you, your change will be: $0.70
You will be given:
2x $0.25
1x $0.1
1x $0.05
4x $0.01

```

As you can see, it's only giving me $0.69 back in change instead of $0.70 .  : (

Here's the code for the program I wrote:
[PHP]
#! /usrn/bin/python
# Filename: change.py


_owe = float(input('How much you owe: '))
_gave = float(input('How much you gave: '))



# This portion of the code makes sure that input _gave
# will be enough money to cover what you owe.

if _owe > _gave:
    _difference = float(_owe) - float(_gave)
    print ('Insufficient funds. You still need to give $%.2f') % _difference
    _addition = int(input('How much will you add? '))
    _gave += _addition
if _owe > _gave:
    print('I\'m sorry but that is not enough. Please start washing dishes \nto earn back the $%.2f that you owe.') %_owe

# This part will count out how much change to give back
# based on commmon denominations of money.

_ndif = float(_gave) - float(_owe)

if _ndif == 0:
        print ('Thank you, that will be enough.')
        
if _ndif > 0:         
    print ('Thank you, your change will be: $%.2f') %_ndif
    _deno_tr = (100, 50, 20, 10, 5, 1, .25, .1, .05, .01)
    _count = []
    

    for number in _deno_tr:
        _mult = float(_ndif) // float(number)
        if _mult > 0:
            _count.append(dict([(number, _mult)]))
            _ndif = _ndif-(number * _mult)
   
                   
# This part of the script will print
#out the change from the dictionary _count.

    print('You will be given:')             
    for i in range(0,(len(_count))):           
        _value = _count[i].items()[0][0]
        _multiple = int(_count[i].items()[0][1])
        print('{0}x ${1}').format(_multiple, _value)
[/PHP]

So far, I've narrowed down my issue to one part of the code (the 36th Line of the code above):

[PHP]
    _deno_tr = (100, 50, 20, 10, 5, 1, .25, .1, .05, .01)
    _count = []
    

    for number in _deno_tr:
        _mult = float(_ndif) // float(number)
        if _mult > 0:
            _count.append(dict([(number, _mult)]))
            _ndif = _ndif-(number * _mult)
[/PHP]

The issue arises from the floor function that I am using to calculate the number of bills/coins the program will give back.  In certain cases when I use 0.1 and 0.01 within the floor function (eg. variable//0.01) it gives me the floor quotient one less that I am expecting. 

```

>>> 20//.1
199.0
>>> 20/.1
200.0
>>> 20//.01
1999.0
>>> 20/.01
2000.0

```

I think I might be misunderstanding what the floor operator is suppose to do.  I expected that the floor operator is suppose to give me a multiplier that I can use to count the bills.  Eg. 23//10 is 2; so the change will be 2x $20 bills with 3 dollars remaining.  Can someone please clarify what's going on?  I am also be open for any suggestions to get around this issue.

Thank you for your help!

---

### Post by NovaAesa on 2011-05-25
I'm not really sure how the // operator works in Python when used on floating point numbers as I don't program in Python very often. Here's an idea though: when doing your calculations, why don't you work with cents rather than dollars so you are always working with an integral amount?

---

### Post by simeon87 on 2011-05-25
> **NovaAesa said:**
> I'm not really sure how the // operator works in Python when used on floating point numbers as I don't program in Python very often. Here's an idea though: when doing your calculations, why don't you work with cents rather than dollars so you are always working with an integral amount?

This approach is sure to work as we had to do this approach in an assignment one day (also involved computing coins of change).

Integers are a lot more trustworthy in programming languages than floating point numbers. It's quite technical but this article is quite informative: [What Every Computer Scientist Should Know About Floating-Point Arithmetic](http://download.oracle.com/docs/cd/E19957-01/806-3568/ncg_goldberg.html).

---

### Post by 770aky on 2011-05-25
> **simeon87 said:**
> This approach is sure to work as we had to do this approach in an assignment one day (also involved computing coins of change).

Integers are a lot more trustworthy in programming languages than floating point numbers. It's quite technical but this article is quite informative: [What Every Computer Scientist Should Know About Floating-Point Arithmetic](http://download.oracle.com/docs/cd/E19957-01/806-3568/ncg_goldberg.html).

Thanks guys!  Thank you, thank you, thank you... 

It worked!!  I calculated everything with integers by converting into cents.  It all worked out beautifully.  

[PHP]
_owe = input('How much you owe: ')
_gave = input('How much you gave: ')

_owe_cents = int(_owe * 100)
_gave_cents = int(_gave *100)

....


   #Converts everything to cents so that floor operator will work
    #with only integers
    _deno_tr = (10000, 5000, 2000, 1000, 500, 100, 25, 10, 5, 1)
    _count = []
    
    for number in _deno_tr:
        _mult = int(int(_ndif) // int(number))
        if _mult > 0:
            _count.append(dict([(number/100.00, _mult)]))
            _ndif = _ndif - (number * _mult)
[/PHP]


Having the numbers as floats were definitely the source of the issue.  Thanks again for all your help!

---

### Post by The Cog on 2011-05-25
Floats are tricky - you can't rely on them being exact. Close but not exact. The idea of using floor like that is dangerous anyway. I suspect that somewhere along the line, the result is coming out as 19.999... and floor would of course reduce this to 19, not 20.

---

