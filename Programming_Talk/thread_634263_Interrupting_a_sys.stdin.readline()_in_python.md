---
title: "Interrupting a sys.stdin.readline() in python?"
date: 2007-12-07
forum: Programming Talk
---

### Post by martinw89 on 2007-12-07
Hello all,
I've got a quick Python question.  I want to set a time limit on an input.  I'm using the threading.Timer module and sys.stdin.readline() for input.  The only problem is that I don't know what to have the timer do to cancel the input.  Here is a quick program to demonstrate what I mean. ```
#!/usr/bin/env python
#This is the function trying to get an input
def inputtest():
	from sys import stdin
	from threading import Timer
	#Starts a timer that will run the cancel function in 5 seconds
	t = Timer(5.0, cancel)
	t.start()
	#the input line
	variable = stdin.readline()
	#cancels the timer if it can get past the input (ie the user enters something)
	t.cancel()
	print variable

#this function is run by the timer
def cancel():
	#prints canceling to debug and check to make sure the cancel function actually runs
	print "canceling"
	#trie a sys.exit() to clear out of sys.stdin.readline()
	from sys import exit
	exit(0)

def main():
	inputtest()

if __name__ == "__main__":
	main()
```

In this example i tried sys.exit(0) to cancel out of the sys.stdin.readline() but with no success.

Am I approaching this correctly?  Thanks for any help.

---

