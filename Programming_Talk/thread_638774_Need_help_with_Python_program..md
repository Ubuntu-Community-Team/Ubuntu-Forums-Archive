---
title: "Need help with Python program."
date: 2007-12-12
forum: Programming Talk
---

### Post by SuperCow56 on 2007-12-12
```
'readNwriteFile.py'


print " Do you want to read an existing file? or create a new file?"
 
choice = raw_input("\n\nPress 'A' to read an existing file. \n\n Press 'B' to create a new file.")
print " You chose " ,choice, "."	



if choice == a:

		fname = raw_input('Enter filename: ')
		print

		try:
			fobj = open(fname, 'r')
		except IOError, e:
			print "*** file open error:", e
		else:
			for eachLine in fobj:
				print eachLine,
			fobj.close()
if choice == b:

	import os
	ls = os.linesep

	# get filename
	while True:

		fname = raw_input('Enter file name: ')
		if os.path.exists(fname):
			print "ERROR: '%s' already exists" % fname
		else:
			break
	
	all = []
	print "\nEnter lines ('.' by itself to quit). \n"
	
	while True:
		entry = raw_input('> ')
		if entry == '.':
			break
		else:
			all.append(entry)
	
	# write lines to file with proper line-ending
	fobj = open(fname, 'w')
	fobj.writelines(['%s%s' % (x, ls) for x in all])
	fobj.close()
	print "DONE!"
else:
	print "\n\nInvalid Option."
	
raw_input("\n\nPress enter to end program.")


```

---

### Post by LaRoza on 2007-12-12
What do you need help with?

(I do see problems, but I am not going to guess the intention of the program, rewrite it, or guess what the OP's problem is)

---

### Post by pmasiar on 2007-12-12
I can see errors:
if choice == 'a' # raw_input() reads a string
possibly you want also lower() input, just in case if someone has CapsLock :-)

It might hel if you tell us what output you expected, what you've got and error messages, if any.

---

### Post by Majorix on 2007-12-12
This is both a very poorly written code and a very poorly written post. Your program has lots of syntax errors and you didn't even specify what you need help with. Sorry.

---

### Post by SuperCow56 on 2007-12-12
It won't allow choice to accept neither 'a' nor 'b'

says " choice = a  is not defined."

---

### Post by Majorix on 2007-12-12
If you don't quote a or b, the interpreter thinks they are variables and looks in your code for a reference to these variables, and if it cannot find any, it will throw errors like it did in your case.

You have to double or single quote a and b for the program to work. But there are other syntax errors I spotted. Please run your code and post the error outputs here.

---

### Post by SuperCow56 on 2007-12-12
Thanks Majorix, all it needed to work on my computer was putting 'a' instead of a.

I know this is poorly written, was just in a hurry to get in done as a school assignment.

---

### Post by Majorix on 2007-12-12
Glad it worked. I misinterpreted this line
```
fobj.writelines(['%s%s' % (x, ls) for x in all])
```
to be a possible bug, because there was no ls in sight. I have done a search in Firefox and it found it so it must work :)

Good luck with your school.

---

