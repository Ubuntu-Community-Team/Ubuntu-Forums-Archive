---
title: "New to Python"
date: 2009-02-03
forum: Programming Talk
---

### Post by COMTIBoy on 2009-02-03
Hi Everyone,

I'm new to Python.

I have just assigned the following string to x.  (x was read from a file)


x = 'F0F0F1F1F0F0F1F1'

but I would like to transpose x to this:

'\xF0\xF0\xF1\xF1\xF0\xF0\xF1\xF1'

I was thinking about creating a function that would take a string (e.g. x) as input and return '\xF0\xF0\xF1\xF1\xF0\xF0\xF1\xF1' as output.

Just not sure what's the most efficient way to put the '\x' in front of each hex value. 

Any tips for a new comer is surely welcomed !
THanks,

---

### Post by unutbu on 2009-02-03
If you can guarantee that 'F' is the first character of every hex value and 'FF' never appears, then you could
use the string method replace() to sneak a r'\x' in front of every 'F':

(The r in r'\x' tells python to interpret '\x' as a raw string. In other words, it tells python to not try to interpret the backslash as a special character.)
[PHP]
#!/usr/bin/env python
x='F0F0F1F1F0F0F1F1'
print x
x=x.replace('F',r'\xF')
print x[/PHP]

If you can guarantee that every hex value is composed of two characters, then:

[PHP]#!/usr/bin/env python
x='F0F0F1F1F0F0F1F1'
print x
y=['']                    # y is a list, first element is an empty string
while x:
    y.append(x[:2])       # append two characters from x 
    x=x[2:]               # chop off the first two characters from x
print y
# ['', 'F0', 'F0', 'F1', 'F1', 'F0', 'F0', 'F1', 'F1']    # This is y
y=r'\x'.join(y)           # join the elements of y together to form a string
                          # use r'\x' as the adjoining string
print y
# \xF0\xF0\xF1\xF1\xF0\xF0\xF1\xF1[/PHP]

---

### Post by wmcbrine on 2009-02-03
x.decode('hex')

---

### Post by COMTIBoy on 2009-02-03
Thanks. Every hex value is two characters so the second option will work.

Thanks again

---

### Post by COMTIBoy on 2009-02-03
I just saw wmcbrine's reply. 

x.decode('hex') works perfect. Thanks!

---

