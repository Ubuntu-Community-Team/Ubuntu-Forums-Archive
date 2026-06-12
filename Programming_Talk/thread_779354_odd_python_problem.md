---
title: "odd python problem?"
date: 2008-05-02
forum: Programming Talk
---

### Post by ricky_cullen on 2008-05-02
i have written a python script to help me speed up how long it takes me to do my math homework, however it refuses to work right.
Here is the code

import math
print "to convert from radians to degrees\
use p as pi"
p=math.pi 
x=raw_input("enter you radians here ")
y=math.radians(x)
print y

i get the output as 

file "test.py", line 6, in <module>
    y=math.radians(x)
TypeError: a float is required


Do note i look at the sticky about homework and i'm not trying to braek any rules i've converting degrees into radians for a while now i just want to speed it up a little and push my programming up a little bit.

thanks in advance

---

### Post by aamukahvi on 2008-05-02
Hi,

as it says a float is required so you cannot provide a string.

[PHP]#!/usr/bin/env python

import math
from decimal import Decimal

print "to convert from radians to degrees\
use p as pi"
p=math.pi
x=raw_input("enter you radians here ")
y=math.radians(Decimal(x))
print y
[/PHP]

---

### Post by ricky_cullen on 2008-05-02
ok i see, one of the many things i have to take note of in the world of programming lol. thanks

---

### Post by LaRoza on 2008-05-02
> **ricky_cullen said:**
> i have written a python script to help me speed up how long it takes me to do my math homework, however it refuses to work right.
Here is the code

import math
print "to convert from radians to degrees\
use p as pi"
p=math.pi 
x=raw_input("enter you radians here ")
y=math.radians(x)
print y

i get the output as 

file "test.py", line 6, in <module>
    y=math.radians(x)
TypeError: a float is required


raw_input returns a string. Use float() to convert to a decimal, and int() to convert to an integer.

```

import math
print "to convert from radians to degrees\
use p as pi"
p=math.pi 
x=raw_input("enter you radians here ")
print math.radians(float(x))

    

```

---

### Post by aamukahvi on 2008-05-02
> **LaRoza said:**
> float(x)
Neat! I was sure there had to be an easier way :D

---

### Post by ricky_cullen on 2008-05-02
> **LaRoza said:**
> 
```

import math
print "to convert from radians to degrees\
use p as pi"
p=math.pi 
x=raw_input("enter you radians here ")
try:
    print math.radians(float(x))
except(ValueError):
    print "That is not a number"
    

```
this is the only one that has worked but it spits back that is not a number when i puy in p/2 which is i worked it out to test the program before hand and it is 90 degrees

i responed to aamukahvi responce before i got to try it out, it gave me another error but removed the one i that was stopin me :D which is what i asked for lol

---

### Post by LaRoza on 2008-05-02
> **ricky_cullen said:**
> this is the only one that has worked but it spits back that is not a number when i puy in p/2 which is i worked it out to test the program before hand and it is 90 degrees

i responed to aamukahvi responce before i got to try it out, it gave me another error but removed the one i that was stopin me :D which is what i asked for lol
I don't understand what you are saying. You entered "p/2"? I don't think you want to do that. If you want to express it that way, just enter the number, not "p".

Here is how I would have written it, from your description:

```

import math
print "To convert from radians to degrees."
p=math.pi 
x=raw_input("enter you radians here ")
if x.isdigit():
    print math.radians(p/float(x))
else:
    print "That is not a number"

```

---

### Post by ricky_cullen on 2008-05-02
it gives me the same output but i think i might try to use the unit circle my teacher gave me so it will print out the exact value from it instead of working out the numbers itself becuase the more i look at it i reliaze it might be hard to look at if it is a really long Decimal so it might be easier and better for my purpose. but thanks to both of you you helped me over my frist bump in programming :)

---

### Post by Can+~ on 2008-05-02
[PHP]#!/usr/bin/env python

import sys, math

def readArgs():
	for i in sys.argv[1:]:
		try:
			print i," radians:",float(i)*math.pi/180.0
		except ValueError:
			print "Not a float"

def start():
	if not len(sys.argv[1:]):
		print "Usage:",sys.argv[0],"float1 float2 float3... floatn"
	else:
		readArgs()


if __name__ == "__main__":
	start()
[/PHP]

Normal usage:
```
python radians.py 15 20 17 30
15  radians: 0.261799387799
20  radians: 0.349065850399
17  radians: 0.296705972839
30  radians: 0.523598775598
```

In case of non-float values:
```
python radians.py 15 NOT A FLOAT 30
15  radians: 0.261799387799
NOT  radians: Not a float
A  radians: Not a float
FLOAT  radians: Not a float
30  radians: 0.523598775598
```

In case of no input:
```
python radians.py 
Usage: python radians.py float1 float2 float3... floatn
```

```
./radians.py 
Usage: ./radians.py float1 float2 float3... floatn
```

A bit excessive example. Although, if someone has a better solution than the [FONT="Courier New"]if not len(sys.argv[1:])[/FONT] . Since I don't like using LBYL style.

---

### Post by ricky_cullen on 2008-05-02
wow... i would have never had come up with anything like that :o

---

### Post by Quikee on 2008-05-03
You could also build yourself a custom python based calculator ;)

[PHP]
import math
print "Type 'exit' to exit the program!"
while 1:
	string = raw_input("Calculate: ")
	if string == "exit":
		break
	print eval(string, {"pi":math.pi, "rad":math.radians, "deg":math.degrees}, {})[/PHP]

And use it like:

```
Type 'exit' to exit the program!
Calculate: deg(pi/2)    
90.0
Calculate: deg(pi/2) * 2
180.0
Calculate: pi/2
1.57079632679
Calculate: rad(360)
6.28318530718
Calculate: rad(deg(pi/2))
1.57079632679
Calculate: 

```

---

### Post by ricky_cullen on 2008-05-03
that is cool, i didnt think it would work and still give the output
[php] deg(pi/2)    
90.0[/php]
i went up the wrong and longer path -_-; lol and tried to program as many as possible into it lol it was over 40 lines of code. which is a lot for a frist timer, well besides a game when you guess numbers that the computer picks lol

---

