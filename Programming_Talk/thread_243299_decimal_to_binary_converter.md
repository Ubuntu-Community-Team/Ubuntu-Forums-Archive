---
title: "decimal to binary converter"
date: 2006-08-24
forum: Programming Talk
---

### Post by greyash99 on 2006-08-24
im trying to make a decimal to binary converter.  What I cant get it to do is get the decimal to correspond to its value in my binary list.

#! /usr/local/bin/python
import os
if os.environ['USER']:
        print 'Hello, '+os.environ['USER']
decimal = ["0","1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "20"]
binary = ["0", "1", "10", "11", "100", "101", "110", "111", "1000", "1001", "1010", "1011", "1100", "1101", "1110", "1111", "10000", "10001", "10010", "10011", "10100"]
hexa = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f", "10", "11", "12", "13", "14"]
print "select your conversion"
print "1 decimal to binary"
print "2 decimal to hexadecimal"
print "3 binary to decimal"
print "4 binary to hexadecimal"
print "5 hexadecimal to decimal"
print "6 hexadecimal to binary"
conversion = input(">")
if conversion == 1:
	number = float(raw_input("what number?")
	
	print binary

---

### Post by ciscosurfer on 2006-08-24
You must have 'bc' installed.  Then try this in a terminal```
echo 'obase=2; ibase=10; 123' | bc
```Enjoy! \\:D/

---

### Post by greyash99 on 2006-08-24
thanks, but I was doing this because I could, not becaue I seriously needed it.  I just wanted to see if I could do it, and got a little stuck :)

---

### Post by ciscosurfer on 2006-08-24
Ok.  Sounds good.  I was just showing you that 'bc' already incorporates these functions.  But good luck with your script!

---

### Post by greyash99 on 2006-08-24
Thanks!=D>

---

### Post by dwblas on 2006-08-28
I don't know if this is what you are talking about, but deicmal to binary would be divide decimal by 2, multiply 1X10 for the whole part of the division and add remainder, so something like

.whole, remain = divmod( int_number, 2 )
.binary_number = 1
.for j in range( 0, whole ) :
.....binary_number *= 10
.binary_number += remain

Haven't thought this through though because I'm not sure you are still interested.

---

### Post by chonger on 2006-08-29
Google is your friend. 

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/219300](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/219300)

Are you trying to do this by creating a table of int to binary mapping? If so, I don't see why it wouldn't work.

---

