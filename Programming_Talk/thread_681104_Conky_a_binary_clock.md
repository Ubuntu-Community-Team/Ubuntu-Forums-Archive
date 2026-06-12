---
title: "Conky a binary clock?"
date: 2008-01-28
forum: Programming Talk
---

### Post by fedex1993 on 2008-01-28
okay from the looks of it i havnt seen one good widget program nada of a binary clock for linux at all or windows. From what i was thinking everyone knows how conky displays bars time and also pictures now to(which i think is amazing) for the desktop. I was thinking about making a binary clock or a binary script that conky can run to show a binary clock. I didnt know if this was the right place but you can move it if yall want. If you would like to help out the project it self and help me get it started PM or post here.

Thanks 

Fedex

---

### Post by fedex1993 on 2008-01-29
Anyone thought about helping anyone ?

---

### Post by Xavieran on 2008-01-29
What is a binary clock?
Do you mean Unix time from the epoch?

My father wrote a binary clock once...

---

### Post by LaRoza on 2008-01-29
> **Xavieran said:**
> What is a binary clock?
Do you mean Unix time from the epoch?

My father wrote a binary clock once...

[http://www.thinkgeek.com/homeoffice/lights/59e0/](http://www.thinkgeek.com/homeoffice/lights/59e0/)

They are cool clocks.

(I want one)

<edit>
[Just bought this one]("http://www.amazon.com/Binary-Clock-Classic-Black-Red/dp/B000IZEL2K/ref=pd_bbs_sr_4?ie=UTF8&s=electronics&qid=1201654622&sr=8-4")

---

### Post by stevescripts on 2008-01-29
Simple code for binary clocks (tcl/tk):

[http://wiki.tcl.tk/12282](http://wiki.tcl.tk/12282)

Not my code, but quick and cute.

Steve
(this doesn't really relate to conky, but I couldn't resist ...)

---

### Post by PaulFr on 2008-01-30
This comment has nothing to do with clocks, but with the ability to display things on the Ubuntu desktop : use or search for **gdesklets** (GNOME) or **superkaramba** (KDE) to see whether there are any widgets meeting your requirements.

---

### Post by Rick_Weber on 2011-05-26
Here's a python script I wrote this morning to solve this problem. I wanted a simple text output like this:

H: 	000010
M: 	101101
S: 	110101

(i.e. 2:45:53)

Here's binary_clock.py. It'll be pretty easy to modify the output to do what you like.

```

# binary_clock.py 
# v0.1
# A python script to display the time in binary format
# Created May 26, by Rick Weber

# Import the math and appropriate time modules.
import math
import time

# positions(time, X) will determine the highest binary position (up to the Xth
# position). For example (32, 7) should return 6.
def positions(number, X=7):
	for i in range(X):
		if number < 2**i:
			return i

# This function will convert a number to a string representation of the binary.
def printBinary(posNum, X=6):
	number = 0
	for i in range(X):
		result = positions(posNum, X+1) - 1
		number = number + 10**(result)
		posNum = posNum - 2**result
	number = "%06d" % number # Convert to string with leading zeros to
	# six digits.
	return number

def printOutput(name, number):
	number = printBinary(int(number))
	print name, "\t", number

def printClock():
	printOutput('H:', time.strftime('%H'))
	printOutput('M:', time.strftime('%M'))
	printOutput('S:', time.strftime('%S'))

printClock()

```

After you've got that printing the output you want, save it and add this to your .conkyrc
```
${execi 0.5 python ~/path/to/binary_clock.py}

```

Cheers,
Rick

---

### Post by Rick_Weber on 2011-05-26
I've made a v0.2 that will output only the binary of a given choice (e.g. hour, minute, etc.). That way you can format the output in Conky more easily.

```
#!/usr/bin/env python
# binary_clock.py 
# v0.2
# A python script to display the time in binary format
# Created May 26, by Rick Weber.
# Take input to determine what variable we are looking at, then output for just
# one variable.
# TODO for v0.3, build a help dialog.
# Import the appropriate modules.
import math, time, sys

# Input:
# Using the sys module, accept the arguments passed into the program and assign
# them to the appropriate variable(s).
variable = sys.argv[1]
variable = str(variable)

if variable == 'S': # second
	time = time.strftime('%S')
elif variable == 'M': # minute
	time = time.strftime('%M')
elif variable == 'H': # hour of 24
	time = time.strftime('%H')
elif variable == 'I': # hour of 12
	time = time.strftime('%I')
elif variable == 'p': # AM/PM
	time = time.strftime('%p')
elif variable == 'w': # day of week
	time = time.strftime('%w')
elif variable == 'd': # day of month
	time = time.strftime('%d')
elif variable == 'j': # day of year
	time = time.strftime('%j')
elif variable == 'U': # week of year
	time = time.strftime('%U')
elif variable == 'm': # montt
	time = time.strftime('%m')
elif variable == 'y': # year YY
	time = time.strftime('%y')

# positions(time, X) will determine the highest binary position (up to the Xth
# position). For example (32, 7) should return 6.
def positions(number, X=7):
	for i in range(X):
		if number < 2**i:
			return i

# This function will convert a number to a string representation of the binary.
def printBinary(posNum, X=6):
	number = int(0)
	for i in range(X):
		result = positions(posNum, X+1) - 1
		number = number + 10**(result)
		posNum = posNum - 2**result
	number = "%06d" % number # Convert to string with leading zeros to
	# six digits.
	print number

printBinary(int(time))

```

And in your conky:
```
Hour:$alignr${execi 0.5 python ~/path/binary_clock.py H}
Minute:$alignr${execi 0.5 python ~/path/binary_clock.py M}
Second:$alignr${execi 0.5 python ~/path/binary_clock.py S}

Day:$alignr${execi 0.5 python ~/path/binary_clock.py d}
Month:$alignr${execi 0.5 python ~/path/binary_clock.py H}
Year:$alignr${execi 0.5 python ~/path/binary_clock.py y}

```

---

