---
title: "How to resolve NameError ?"
date: 2010-12-09
forum: Programming Talk
---

### Post by navaneethan on 2010-12-09
i am new to this python which i had written a simple program to read a file as well as to write it as we use in java

May i know the problem with this program?

let me knowit

```
import sys
import traceback

class Myfinally:
	def __init__(self,name='text.txt',data='nava'):
		self.name=name
		self.data=data
		f=file(name,'w')
		f.write(data)
		return 'succ worte'
	def read(self,name):
		self.name=name
		f.file(name)
		return f.readlines
	
	try:
		
		name=raw_input('Enter file name:')
		data=raw_input('Enter something:')
		myf = Myfinally()
		myf(name,data)
		print "If yu wannaread press 1"
		ch=int(raw_input("1 or 0"))
		if ch == 1:
			myf.read(name)
			sys.exit()
		else:
			print "I think name is wrong"
	except Exception as inst:
		print inst.args
		print inst
		print type(inst)	
		print sys.exc_info()	
		traceback.print_exc(file=sys.stdout)
```

---

### Post by surfer on 2010-12-09
i did not run the thing, but f.readlines should be f.readlines() .

and are you sure you want __init__ to write a file? constructors should (in general) only be used to initialize things.

---

### Post by surfer on 2010-12-09
ok, i ran it. this should work, but why do you pass 'name' as a parameter when it's a member of Myfinally?

```

import sys
import traceback

class Myfinally:
	def __init__(self,name='text.txt',data='nava'):
		self.name=name
		self.data=data
		f=file(name,'w')
		f.write(data)
		# return 'succ worte'



	def read(self,name):
		self.name=name
		f = file(name)
		return f.readlines()
	
	

if __name__ == '__main__':

    try:
        name=raw_input('Enter file name:')
	data=raw_input('Enter something:')
	myf = Myfinally(name,data)
	print "If yu wannaread press 1"
	ch=int(raw_input("1 or 0"))
	if ch == 1:
		print myf.read(name)
		sys.exit()
	else:
		print "I think name is wrong"
    except Exception as inst:
	print inst.args
	print inst
	print type(inst)	
	print sys.exc_info()	
	traceback.print_exc(file=sys.stdout)

```

---

### Post by surfer on 2010-12-09
by the way: have a look at [python's with statement]("http://docs.python.org/release/2.5.2/ref/with.html") (nice [totorial]("http://effbot.org/zone/python-with-statement.htm")) which hanldes the try, except, finally stuff for you.

---

### Post by navaneethan on 2010-12-09
ya sure i ll define it in seperate module

---

### Post by navaneethan on 2010-12-09
eventually only i done it;at first i have passed as a parameter to the main function

---

