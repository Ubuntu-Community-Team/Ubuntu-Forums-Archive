---
title: "Python 2.7 Binary Translator Help"
date: 2011-05-30
forum: Programming Talk
---

### Post by alapoo on 2011-05-30
I have to admit, I've only been using python 2.7 for about a week now so my skills aren't very deep but I figured I'd try to write a program on my own to test what I've learned.

I'm having issues with this program which is meant to translate any number <255 into binary.

```

## This program converts binary numbers into any number available in 8 bits.

print ('This 8-bit decimal to binary translator can translate any number between 0 & 255')
orgnumber = raw_input()

## Check
if orgnumber > 255:
 print ('Please type a number between 0 & 255')
 orgnumber = raw_input()
else:
 orgnumber = number

## 128 / 2.7
if number > 127:
 number = number - 128
 seven = 1
else:
 seven = 0
 
## 64 / 2.6
if number > 64:
 number = number - 64
 six = 1
else: 
 six = 0

## 32 / 2.5
if number > 32:
 number = number - 32
 five = 1
else: 
 five = 0

## 16 / 2.4
if number > 16:
 number = number - 16
 four = 1
else: 
 four = 0

## 8 / 2.3
if number > 8:
 number = number - 8
 three = 1
else: 
 three = 0

## 4 / 2.2
if number > 4:
 number = number - 4
 four = 1
else: 
 four = 0

## 2 / 2.1
if number > 2:
 number = number - 2
 one = 1
else: 
 one = 0

## 1 / 2.0
if number > 1:
 number = number - 1
 zero = 1
else: 
 zero = 0

print str('seven')+str('six')+str('five')+str('four') + ' ' + str('three')+str('two')+str('one')+str('zero')

```

I'm using conditional statements for everything which probably isn't the best way to do it but it's simply how my brain works without being trained in programming.  I'm open to any suggestions.

---

### Post by johnl on 2011-05-30
You can do this (very) easily using the string.format function with the 'b' (binary) [format specifier](http://docs.python.org/library/string.html#formatspec):

```

n = raw_input('enter a number: ')
print '{0:b}'.format(n)

```

If you want to do it yourself, you can write it more succinctly with a loop using bit operations:

```

def to_binary(n):
    if n == 0:
        return '0'
    # rc is our string representation
    rc = ''
    # loop until all the bits are clear
    while n != 0:
            # if the lowest bit is set, prepend a 1, otherwise 0
            # we add at the front because we are doing the bits in 
            # reverse order, from least significant to most significant
            rc = ('1' if n & 1 else '0') + rc
            # shift the bits to the right by one
            n >>= 1
    return rc

```

---

### Post by alapoo on 2011-05-30
that code returns me error:

```

Traceback (most recent call last):
  File "bit.py", line 2, in <module>
    print '{0:b}'.format(n)
ValueError: Unknown format code 'b' for object of type 'str'

```

is this option available under python 2.7?

I downloaded python3.2 the other day but I've been using google code tutorials to learn python which teach using python 2.7.

---

### Post by johnl on 2011-05-30
> **alapoo said:**
> that code returns me error:


Apologies, you need to coerce the return from raw_input() to an integer before passing it to format():

```

n = int(raw_input('...: '))

```

---

