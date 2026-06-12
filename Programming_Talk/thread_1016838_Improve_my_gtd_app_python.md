---
title: "Improve my gtd app python"
date: 2008-12-20
forum: Programming Talk
---

### Post by matmatmat on 2008-12-20
I've created a gtd app in python:

```

#! /usr/bin/env python
# -*- coding: utf8 -*-
#########imports#########
from sys import exit
from os import system
import string
#########main#########
while True:
	print "#########pyGTD#########"
	print "Your options are:"
	print "1) View tasks"
	print "2) Add a task."
	print "3) Quit"
	print "#######################\n\n"
	
	c = raw_input("pyGTD>")
	
	#view
	if c == "1":
		f = open("todo.txt", "r")
		system("clear")		
		print "Tasks:"
		lines = f.read()
		print lines
		print "\n\n\n"
		
	
	#add
	elif c == "2":
		f = open("todo.txt", "a")
		system("clear")
		n = raw_input("Enter the name of the task: ")
		s = raw_input("Enter a summary of the task: ")
		p = raw_input("Enter the priority of the task (high, medium, low): ")
		st = raw_input("Enter the date/time started: ")
		fi = raw_input("Enter the date/time to be done by: ")
		f.write("######Name: " + n + "######\nSummary: " + s + "\nPriority: " + p + "\nDate/time started: " + st + "\nDate/time to be finished " + fi + "\n\n")
		f.close()
	
	#quit
	elif c == "3":
		system("clear")
		exit()
		

```
how could it be improved?
Please help

---

### Post by Tony Flury on 2008-12-20
If you want to improve the coding, but not change what it does : 
[LIST]
[*]Modularize it - make the operations functions
[*]Look at using pickle - makes it easy to read in and out - and makes the todo list non-human readable - if you like some simple security.
[/LIST]

New functionality : 
[LIST=1]
[*] Error checking - what happens if the user enters a invalid date for example ?
[*] Sensible defaults - (start date defaults to today)
[*] Ability to mark tasks as complete - or cancelled ?
[*] Relative dates - Enter Start date as +2, means the day after tomorrow
[*] Simple command line interface - to avoid going through the menus and prompts - pyGTD add "My task" "My Task Summary" +1 +7 - adds a task called My task that starts tomorrow and needs to be completed in 7 days time.
[*] Reminders - some how  ?
[/LIST]

---

### Post by matmatmat on 2008-12-21
I just thought I'd post a new version:
```

#! /usr/bin/env python
# -*- coding: utf8 -*-
######### imports #########
from sys import exit
import sys
from os import system
import string
import datetime
######### functions #######


def view():
	f = open("todo.txt", "r")
	system("clear")		
	print "Tasks:"
	lines = f.read()
	print lines
	print "\n\n\n"	


def new():
	f = open("todo.txt", "a")
	system("clear")
	n = raw_input("Enter the name of the task: ")
	s = raw_input("Enter a summary of the task: ")
	p = raw_input("Enter the priority of the task (high, medium, low): ")
	st = raw_input("Enter the date/time started: ")
	fi = raw_input("Enter the date/time to be done by: ")
	f.write("######Name: " + n + "######\nSummary: " + s + "\nPriority: " + p + "\nDate/time started: " + st + "\nDate/time to be finished " + fi + "\n\n")
	f.close()
	
	
def usage():
	print "Usage:"
	print "pyGTD options"
	print "Options:"
	print "[-a] add a task:"
	print "	pyGTD -a name summary priority date/time_started date/time_to_be_finished_by"
	print "[-v] view tasks"
	print "[-h] view this help message"
	print "nothing: goes into prompt"

######### main #########



# arguments passed?
if len(sys.argv) >= 2:
	#there has been arguments passed
	if sys.argv[1] == "-v":
		view()
	elif sys.argv[1] == "-a":
		f = open("todo.txt", "a")
		f.write("######Name: " + sys.argv[2] + "######\nSummary: " + sys.argv[3] + "\nPriority: " + sys.argv[4] + "\nDate/time started: " + sys.argv[5] + "\nDate/time to be finished " + sys.argv[6] + "\n\n")
	elif sys.argv[1] == "-h":
		usage()
	else:
		usage()
		
else:	
	#no arguments passed
	
	while True:
		print 
		print "#########pyGTD#########"
		print "Your options are:"
		print "1) View tasks"
		print "2) Add a task"
		print "3) Quit"
		print "#######################\n\n"
		
		c = raw_input("pyGTD>")
		
		#view
		if c == "1":
			view()
			
		
		#add
		elif c == "2":
			new()
				
		#quit
		elif c == "3":
			system("clear")
			exit()
		

```

---

### Post by Tony Flury on 2008-12-21
why not make the new function take arguments, which are optional - and then you can use the same function from both the command line and the menus ?

---

### Post by matmatmat on 2008-12-21
Heres the new "new" function:
```

def new(prompt):
	f = open("todo.txt", "a")
	system("clear")
	if prompt:
		n = raw_input("Enter the name of the task: ")
		s = raw_input("Enter a summary of the task: ")
		p = raw_input("Enter the priority of the task (high, medium, low): ")
		st = raw_input("Enter the date/time started: ")
		fi = raw_input("Enter the date/time to be done by: ")		
		f.write("######Name: " + n + "######\nSummary: " + s + "\nPriority: " + p + "\nDate/time started: " + st + "\nDate/time to be finished " + fi + "\n\n")
	
	else:
		f.write("######Name: " + sys.argv[2] + "######\nSummary: " + sys.argv[3] + "\nPriority: " + sys.argv[4] + "\nDate/time started: " + sys.argv[5] + "\nDate/time to be finished " + sys.argv[6] + "\n\n")
	f.close()

```

---

### Post by matmatmat on 2008-12-21
How would I check if the users dates are in a correct format?
Would I use the date module?

---

### Post by Tony Flury on 2008-12-21
yep - i think that the datetime module contains validation methods (never used it myself though) - although it is relatively easy to spin your own method that takes a date and confirms that it is in a valid format. I used to give it as a class exercise when i taught programming.

---

### Post by matmatmat on 2008-12-21
Thanks! :)

---

### Post by snova on 2008-12-21
> **matmatmat said:**
> Heres the new "new" function:
```

def new(prompt):
	f = open("todo.txt", "a")
	system("clear")
	if prompt:
		n = raw_input("Enter the name of the task: ")
		s = raw_input("Enter a summary of the task: ")
		p = raw_input("Enter the priority of the task (high, medium, low): ")
		st = raw_input("Enter the date/time started: ")
		fi = raw_input("Enter the date/time to be done by: ")		
		f.write("######Name: " + n + "######\nSummary: " + s + "\nPriority: " + p + "\nDate/time started: " + st + "\nDate/time to be finished " + fi + "\n\n")
	
	else:
		f.write("######Name: " + sys.argv[2] + "######\nSummary: " + sys.argv[3] + "\nPriority: " + sys.argv[4] + "\nDate/time started: " + sys.argv[5] + "\nDate/time to be finished " + sys.argv[6] + "\n\n")
	f.close()

```

I don't think that's quite what was meant... rather, have new() take arguments, such as:

[PHP]def new(name, summary, priority, startDate, doneDate):[/PHP]

And have the calling code do the prompting.

Or, if you want a challenge, use dictionaries mapping parameter names to prompt strings, and define a generic function to prompt for each value, and call the function with ** syntax. :)

---

### Post by matmatmat on 2008-12-22
Thanks everyone! Here is the new code:
```

#! /usr/bin/env python
# -*- coding: utf8 -*-
######### imports #########
from sys import exit
import sys
from os import system
import string
import datetime
######### functions #######


def view():
	f = open("todo.txt", "r")
	system("clear")		
	print "Tasks:"
	lines = f.read()
	print lines
	print "\n\n\n"	


def new(prompt):
	f = open("todo.txt", "a")
	system("clear")
	if prompt:
		n = raw_input("Enter the name of the task: ")
		s = raw_input("Enter a summary of the task: ")
		p = raw_input("Enter the priority of the task (high, medium, low): ")
		st = raw_input("Enter the date/time started: ")
		fi = raw_input("Enter the date/time to be done by: ")		
		f.write("######Name: " + n + "######\nSummary: " + s + "\nPriority: " + p + "\nDate/time started: " + st + "\nDate/time to be finished " + fi + "\n\n")
	
	else:
		f.write("######Name: " + sys.argv[2] + "######\nSummary: " + sys.argv[3] + "\nPriority: " + sys.argv[4] + "\nDate/time started: " + sys.argv[5] + "\nDate/time to be finished " + sys.argv[6] + "\n\n")
	f.close()
	
	
def usage():
	print "Usage:"
	print "pyGTD options"
	print "Options:"
	print "[-a] add a task:"
	print "	pyGTD -a name summary priority date/time_started date/time_to_be_finished_by"
	print "[-v] view tasks"
	print "[-h] view this help message"
	print "[-r] remove all tasks"
	print "nothing: goes into prompt"

def remove():
	f = open("todo.txt", "w")
	f.write("")
	f.close()
	
######### main #########



# arguments passed?
if len(sys.argv) >= 2:
	#there has been arguments passed
	if sys.argv[1] == "-v":
		view()
	
	elif sys.argv[1] == "-a":
		new(False)
	
	elif sys.argv[1] == "-h":
		usage()
	
	elif sys.argv[1] == "-r":
		remove()

	else:
		usage()
		
else:	
	#no arguments passed
	
	while True:
		print 
		print "#########pyGTD#########"
		print "Your options are:"
		print "1) View tasks"
		print "2) Add a task"
		print "3) Remove all tasks"
		print "4) Quit"
		print "#######################\n\n"
		
		c = raw_input("pyGTD>")
		
		#view
		if c == "1":
			view()
			
		
		#add
		elif c == "2":
			new(True)
				
		#remove all
		elif c == "3":
			system("clear")
			remove()
		
		#exit
		elif c == "4":
			system("clear")
			exit()
		

``` 
You never know, one day it might be a program someone would want to use!
(Optimism):lolflag:
Feel free to comment (good or bad)!

---

### Post by Tony Flury on 2008-12-22
of course now - your remove deletes all tasks in that folders task list. What about if you want to remove one ?

Hint : it is easier to remove individual lines if they are all in a list

And also - what happens if i create a load of tasks and then change to another folder - if i now run the application the task list is empty because it uses todo.txt in the current folder. so i have to remember which folder i was in when i first ran the application.

try thinking about storing todo.txt in a hidden folder in the users home folder (say ~/.pyGTD) - so it then does not matter where you are when you run the application - you always get the same task list.

---

### Post by matmatmat on 2008-12-23
Thanks for the tips! I put the main script in /usr/bin and put todo.txt somewhere else, can't remember where. :)
Would I have to save the tasks as one line?

---

### Post by Tony Flury on 2008-12-23
you can use whatever format you want so long as you read it out in the same way.

I suggested using the pickle format as a simple way of writing data into and out of file, without you as the code having to worry about the actual data format within the file - the pickle module takes care of all of that. You can also use pickle for a variety of other methods, but saving data into files is a good use of it.

The reason i suggested storing todo.txt in a hidden folder in the users home directory is that way, if you have more than one user on the system, then they can each have their own task list, since they each have their own todo.txt.

---

### Post by matmatmat on 2008-12-23
I'll try using pickle...
Meanwhile here's the new code:
```

#! /usr/bin/env python
# -*- coding: utf8 -*-
######### imports #########
from sys import exit
import sys
from os import system
import string
import datetime
######### functions #######


def view():
	f = open("todo.txt", "r")
	system("clear")		
	print "Tasks:"
	lines = f.read()
	print lines
	print "\n\n\n"	


def new(prompt):
	f = open("todo.txt", "a")
	system("clear")
	if prompt:
		n = raw_input("Enter the name of the task: ")
		s = raw_input("Enter a summary of the task: ")
		p = raw_input("Enter the priority of the task (high, medium, low): ")
		st = raw_input("Enter the date/time started: ")
		fi = raw_input("Enter the date/time to be done by: ")		
		f.write("######Name: " + n + "###### Summary: " + s + " Priority: " + p + " Date/time started: " + st + " Date/time to be finished " + fi + "\n")
	
	else:
		f.write("######Name: " + sys.argv[2] + "###### Summary: " + sys.argv[3] + " Priority: " + sys.argv[4] + " Date/time started: " + sys.argv[5] + " Date/time to be finished " + sys.argv[6] + "\n")
	f.close()
	
	
def usage():
	print "Usage:"
	print "pyGTD options"
	print "Options:"
	print "[-a] add a task:"
	print "	pyGTD -a name summary priority date/time_started date/time_to_be_finished_by"
	print "[-v] view tasks"
	print "[-h] view this help message"
	print "[-r] remove all tasks"
	print "nothing: goes into prompt"

def remove():
	f = open("todo.txt", "w")
	f.write("")
	f.close()
	
def remove_one(prompt):
	f = open("todo.txt", "r")
	system("clear")
	b = 1
	a = []
	if prompt:
		for line in f:
			print str(b) + " " + line
			a.append(line)
			b = b + 1
		r = raw_input("Enter the line you want to delete (numbers on the left): ")
	else:
		for line in f:
			a.append(line)		
		r = sys.argv[2]
	re = int(r)
	re = re - 1
	a.pop(re)
	f.close()
	f = open("todo.txt", "w")
	le = len(a)
	for i in range(0,le):
		f.write(a[i])
		
	
######### main #########



# arguments passed?
if len(sys.argv) >= 2:
	#there has been arguments passed
	if sys.argv[1] == "-v":
		view()
	
	elif sys.argv[1] == "-a":
		new(False)
	
	elif sys.argv[1] == "-h":
		usage()
	
	elif sys.argv[1] == "-r":
		remove()
	
	elif sys.argv[1] == "-re":
		remove_one(False)

	else:
		usage()
		
else:	
	#no arguments passed
	
	while True:
		print 
		print "#########pyGTD#########"
		print "Your options are:"
		print "1) View tasks"
		print "2) Add a task"
		print "3) Remove all tasks"
		print "4) Remove one task"
		print "5) Quit"
		print "#######################\n\n"
		
		c = raw_input("pyGTD>")
		
		#view
		if c == "1":
			view()
			
		
		#add
		elif c == "2":
			new(True)
				
		#remove all
		elif c == "3":
			system("clear")
			remove()
		
		elif c == "4":
			system("clear")
			remove_one(True)
		
		#exit
		elif c == "5":
			system("clear")
			exit()
		

		

```
Thanks again!
How would I get the users home dorectory

---

### Post by snova on 2008-12-23
[PHP]>>> import os
>>> os.environ['HOME']
'/home/snova'
>>>[/PHP]

---

### Post by Tony Flury on 2008-12-23
ok - a users home directory is given by the path "~" - but you need to **_expand_** it before you can use it in things like os.open() etc - look at the os.path module for inspiration :-)

pickle is incredibly simply to use - but you will need to change your code design if you want to use it.

Essentially your code will open and use pickle to read the todo file into a list - and then you will do all your operations on the list (including adding, removing, viewing, and clearing), and then when your program exits it will use pickle to write the whole list back to the todo file.

I would suggest that your list should actually be constructed of tuples (essentally a complex data type) - if you do this it actually opens up some very interesting capabilities :
1) you can now display the tasks in a different format to the format you save it in - so you could for instance do a quick summary, with only some of the fields, or do a multiple line view.
2) you can easily edit a task - you just change one element of the tuple.
3) You can easily do searches on the list, because each field is held seperately to the others
4) building on number 3 - you can do filters - show me all the tasks that are late

this will not only make your tool far more powerful - it will also give you a chance to play with lists and tuples - which are incredibly powerful parts of python : 

[http://docs.python.org/library/stdtypes.html#sequence-types-str-unicode-list-tuple-buffer-xrange](http://docs.python.org/library/stdtypes.html#sequence-types-str-unicode-list-tuple-buffer-xrange)

and if you have not already done so - bookmark [http://docs.python.org/](http://docs.python.org/) and work through the tutorial - it will teach you far more than i can do.

---

### Post by matmatmat on 2008-12-24
Thanks, I've made it use ~/.pyGTD/todo.txt as the path to the todos, I'll have a look at pickle but it might be a little beyond me (I'm a newbie to programming- I'm enjoying it though :) ). Once again thanks and any more feedback is appreciated.

---

### Post by matmatmat on 2009-01-29
I've made a launchpad project for this (you may have seen my post about the passwrd generator - that was a test), hopefully beginners, like me, will join in. It can be found [here]("https://launchpad.net/passwrdgenerator"). Please participate!

---

