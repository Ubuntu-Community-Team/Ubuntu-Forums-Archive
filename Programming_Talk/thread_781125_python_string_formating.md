---
title: "python string formating"
date: 2008-05-04
forum: Programming Talk
---

### Post by bschleusner on 2008-05-04
I am working on a program that needs to format a number into a string with a certain number of digits, but I am not good enough with the language to be able to format the number with a dynamic number of digits without creating ugly code.

Here is the code so far....
```
def formatnum(num=0,digits=0):
    
    if (digits == 0):
        return num
    
    if (digits == 1):
        retstr = '%01d' %(num)
    if (digits == 2):
        retstr = '%02d' %(num)
    if (digits == 3):
        retstr = '%03d' %(num)
    if (digits == 4):
        retstr = '%04d' %(num)
    if (digits == 5):
        retstr = '%05d' %(num)
        
    return retstr
```

This is just a quick hack to make the program do what I want, but is there an easier way?

---

### Post by Can+~ on 2008-05-04
fact: You can multiply strings on python:

[PHP]print "hello "*5[/PHP]

produces "hello hello hello hello hello".

Also, if you're interested, strings have a method called "zfill" or zerofill, that can do the following:

```
mystring.zfill(n)
```

so, if you have a "25" with zfill(5), it will produce "00025"; if it is zfill(4) it will be "0025", etc.

I'm not sure what you want to achieve, but I feel that you want to make a zfill. There are a lot of fancy methods for strings, don't fear to [check the doc]("http://docs.python.org/lib/string-methods.html")

---

### Post by LaRoza on 2008-05-04
```

def short(num=0,digits=0):
    return str(num).zfill(digits)

```

Does the same thing as the long one, but more flexible.

---

### Post by deuce868 on 2008-05-04
This also works to build the formatting string first, and then use it.

It's a little more flexible since you can do more than just zero pad with zfill. You can basically build any formatting string you wish. 

```
 
def output(num, digits):
    string = '%%0%dd' % digits
    
    # if called output(3,3) this string is %03d
    print string 
    
    # and then this should output 003
    print string % num 

```

---

### Post by bschleusner on 2008-05-04
Wow, zfill is exactly what I needed. Thanks!

---

