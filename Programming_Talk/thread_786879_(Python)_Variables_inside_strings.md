---
title: "(Python) Variables inside strings"
date: 2008-05-08
forum: Programming Talk
---

### Post by durand on 2008-05-08
Is it possible in python to print a string with variables embedded inside it. I'm new to python so I'm not even sure how you would show that some word is a variable except when they are separate.

Ex:

print "Hello var1. You are in var2, etc."


I've seen print " "hello %s" % name " being used but I'm not sure how to add more text and variables.

My actual problem is that I need to print this line into a file.

```
<smiley shortcut=':)' checksum='d224f5890bad7f01e766cbcb9184d4703b65f413' filename='smile.png'/>
```

...where the values for shortcut, checksum and filename are variables in my python script.

Thanks.

---

### Post by LaRoza on 2008-05-08
> **durand said:**
> Is it possible in python to print a string with variables embedded inside it. I'm new to python so I'm not even sure how you would show that some word is a variable except when they are separate.



Yes, you can. Example code:

Example code:
```

name = raw_input("What is your name? ")

age = raw_input("What is your age? ")

rank = raw_input("How rank are you? ")

if age.isdigit():
    print "Hello %s, you are %i years old and are %s rank" % (name,int(age),rank)
else:
    print "%s, \"%s\" is not an age!" % (name,age)

```

This sort of thing can be done with strings in many situations. It is similar to printf() in C if you know that language.

```

output = '<smiley shortcut="%s" checksum="%s" filename="%s"/>' % (shortcut,checksum,filename)


```

---

### Post by pmasiar on 2008-05-08
or, more flexible way:

[php]
print "my name is %(name)s and I like %(pet)s" % dict(name='Joe', pet='platypus')
[/php]

---

### Post by durand on 2008-05-08
Awesome. I'll try both ways! Thanks guys.

---

### Post by ki4jgt on 2011-04-06
Is there a way to do this with numerical values and not just text based numbers?

---

### Post by durand on 2011-04-06
That should work with numericals as well. How do you want it to work?

---

### Post by ki4jgt on 2011-04-06
I keep trying this.

```

v = 2011
b = v - 1

print """Happy New Years. Good-bye %v

Further comments. . . blah blah blah""" % (v)
```

I even went as far as to change v and b to v = `v` and b = `b`
> ValueError: unsupported format character 'v' (0x76) at index 7
That's what I get EVERY time. I've tried single quotes, double, triple. I've tried changing v and b to their text version (As stated above)

---

### Post by Arndt on 2011-04-07
> **ki4jgt said:**
> I keep trying this.

```

v = 2011
b = v - 1

print """Happy New Years. Good-bye %v

Further comments. . . blah blah blah""" % (v)
```

I even went as far as to change v and b to v = `v` and b = `b`

That's what I get EVERY time. I've tried single quotes, double, triple. I've tried changing v and b to their text version (As stated above)


You need to use one of the existing conversion specifiers, like %s or %d, depending on the type of the value to be inserted, like in the previous examples in this thread. See [http://docs.python.org/library/stdtypes.html#string-formatting-operations](http://docs.python.org/library/stdtypes.html#string-formatting-operations)

---

### Post by durand on 2011-04-07
```

v = 2011
b = v - 1

print """Happy New Year %s. Good-bye %s

Further comments. . . blah blah blah"""%(v, b)
```

You always use %s and %d which are placeholders and your actual variables go at the end.

---

### Post by andrew1992 on 2011-04-07
Actually those don't need to be used anymore - I find this much easier:

```
print "Hello, {0}! I'm {1} years old".format("John", 18)
```


```
Hello, John! I'm 18 years old.
```

---

### Post by nvteighen on 2011-04-07
> **andrew1992 said:**
> Actually those don't need to be used anymore - I find this much easier:

```
print "Hello, {0}! I'm {1} years old".format("John", 18)
```


```
Hello, John! I'm 18 years old.
```

This was introduced in Python 2.6 and is the only legal way in Python 3.0, which dropped the (weird) way using the % operator. Keep that in mind for the future.

---

### Post by durand on 2011-04-07
Ah, thats much neater than %, which isn't very pythonic...The only thing is that if you plan on sharing your code, others must have python 2.6 or above.

---

### Post by Arndt on 2011-04-07
> **nvteighen said:**
> This was introduced in Python 2.6 and is the only legal way in Python 3.0, which dropped the (weird) way using the % operator. Keep that in mind for the future.

Will it be possible to (re)define the % operator in 3.0 to do what it does in 2.7?

---

### Post by durand on 2011-04-07
Doubt it. 3.x isn't meant to be backwards compatibile with 2.x. Also, isn't % also a modulus operator in normal circumstances. Maybe thats what it has become in 3.x?

---

### Post by wmcbrine on 2011-04-07
> **nvteighen said:**
> This was introduced in Python 2.6 and is the only legal way in Python 3.0, which dropped the (weird) way using the % operator.No it didn't (hasn't). At least not as of 3.1.2...

---

### Post by nvteighen on 2011-04-08
> **wmcbrine said:**
> No it didn't (hasn't). At least not as of 3.1.2...

Yup, you're right, I've tried it on my Python 3.1.3. But I'm sure to have read that somewhere; funny enough, I haven't found it again, so I have probably missed something :|

I apologize for the misinformation.

---

### Post by hotsaucejalapeno on 2012-12-17
Could you not just use the str() statement?  Example:

ticketCost = 10

print "The cost of your ticket is $" + str(ticketCost) + "."

Or is that the same thing?

---

### Post by Bachstelze on 2012-12-17
This works too, it is just very ugly.

---

### Post by Tony Flury on 2012-12-18
> **Bachstelze said:**
> This works too, it is just very ugly.

+1
String formatting is the way to go, a lot more flexibility than using str - since you get all the featurs of the formatting mini-language too.

Using string formatting (using the {0} type format) has the added benefit of being able to be overwritten for custom classes (you simply define a __format__ method for your class): so you can define what a format string of "+02.8d" actually means for your class, or you could even define your own format mini-langauge for your class.

---

