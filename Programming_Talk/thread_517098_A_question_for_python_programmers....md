---
title: "A question for python programmers..."
date: 2007-08-04
forum: Programming Talk
---

### Post by Sir Nose on 2007-08-04
I've been learning Python recently, and I'm noticing my programs tend to look like jagged C code, like talking with a heavy accent. Here's a little routine for generating cellular automata...
```
import Numeric

class CellAutomata:
	def __init__(self, rule):
		self.bits = [ 1, 2, 4, 8, 0x10, 0x20, 0x40, 0x80 ]
		self.rule=rule
		self.row=Numeric.zeros((80)) #init array
		self.oldrow=Numeric.zeros((80)) #init array for previous row of cells
		self.row[40]=1 #first cell
		print 'automata init, rule ' + str(rule)
	def process(self):
		for i in range(len(self.row)):
			self.oldrow[i]=self.row[i]
		for i in range(1,len(self.row)-1):
			x1=i-1
			x2=i+0
			x3=i+1
			v=0
			v |= self.oldrow[x1]<<2
			v |= self.oldrow[x2]<<1
			v |= self.oldrow[x3]
			if self.rule & self.bits[v]:
				self.row[i]=1
			else:
				self.row[i]=0
	def display(self):
		a=''
		for x in range(len(self.row)):
			a+=str(self.row[x])
		print a

CA = CellAutomata(30)

for i in range(25):
	CA.display()
	CA.process()

```

Now, it isn't elegant at all, but it works. How would you improve this, make it more 'pythonic'? Any help is appreciated.

---

### Post by Paul Miller on 2007-08-04
This particular code does a lot of computation and bit-twiddling, and such things often look unnatural in Python because the language isn't well-suited to the task.  The only suggestion I have is to change the display function to:

```

def display (self):
    print ''.join ( [str (row) for row in self.row ] ) 

```

Your version is slower and longer, whereas the ''.join () idiom is well-recognized by Python programmers.

---

### Post by Sir Nose on 2007-08-04
Thanks for the suggestion. You might be right, there's not a lot to improve there, due to nature of this task. The string processing capabilities in Python are amazing though. One of the things that made me finally quit C was that it's so cumbersome in those things.

---

### Post by smartbei on 2007-08-04
Well, the length of self.row seems to be constant, so there is really no need to do len(self.row), unless you are future-proofing.

Another thing - in the first part of the process method you copy all of self.row to self.oldrow. An easier way to do that is self.oldrow=list(self.row). That does copy the list, rather than a reference.

---

### Post by Sir Nose on 2007-08-04
Thanks! That was probably the ugliest part in the routine - in C you could do memcpy() and hide the boring stuff. I was sure that For-loop isn't the right way to do it. *Feels enlightened*

---

### Post by Smygis on 2007-08-04
[http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)
Read and enjoy, Some smal stuff.

---

### Post by pmasiar on 2007-08-04
> **Sir Nose said:**
> my programs tend to look like jagged C code

Python is your friend - trust your types to do the right thing. Check idioms: [http://www.google.com/search?q=python+idioms](http://www.google.com/search?q=python+idioms)

```

# types are smart and know how to print itself:
print 'automata init, rule', rule

# Make "shallow" copy of a list:
# 1) using list slicing
oldrow = row[:] 
# 2) list comprehension
oldrow = [do_something(x) for x in row] 

# loop thru a list with index, skipping zeroth and last item:
for i, cell in enumerate(row[1:-1]):
    print i, cell

# print row:
# 1) avoid spaces as separators:
print ''.join( str(x) for x in row)
# 2) nice comma-and-space separated
print ', '.join( str(x) for x in row)
# 3) using formatting as needed
print ', '.join( "%i" % x for x in row)


```

---

### Post by Sir Nose on 2007-08-04
Hey, thanks a lot. That was really helpful.

---

