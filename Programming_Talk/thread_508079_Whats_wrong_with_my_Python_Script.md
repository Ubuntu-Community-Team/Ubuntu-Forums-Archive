---
title: "Whats wrong with my Python Script"
date: 2007-07-23
forum: Programming Talk
---

### Post by eldara5 on 2007-07-23
Can anyone please tell me whats wrong here, the error is at the bottum part of creating rerun() function

```

#! user/bin/python
#
print #Just for a space

### Creating a new function to rerun the program
def rerun():
	        a = raw_input('Would you like to restart the program?  ')
		while a == 'yes':
			print 'Would you like to lookup a user or add one?,'

			start = raw_input('Type lookup or add:  ') # wait for the user

			if start == 'add':

				print

				name = raw_input("Type the first name: ")

				print

				lname = raw_input('Type the last name: ')

				print 

				age = raw_input('Type the age: ')

				print

				address = raw_input('What is his/her address ?  ')

				print

				Telephone = raw_input('Whats his/her telephone number ?  ')

				print

				print 'Ok, This is what you gave me'

				print

				print 'the name is', name, lname,
				print
				print 'they are ', age, 'years old',
				print
				print 'they live at', address, 
				print
				print 'And there number is', Telephone,

				print

				well = raw_input('is this ok?  ')

				if well == 'yes':
					print 
					print 'Storing Data Now'
				else:
					print
					print 'Why did you put it in wrong???? /n Well im a nice program so i wont save your mistake but now you have to 						start again'
				
					print 'Program Created by Eldara'
					a = raw_intput('Would you like to restart the program?  ')
			        else: 						##ERROR IS HERE <--------------------------------------------
				      	print "Exiting Program Now...."
 
		else: #What happens if they try to lookup
			print 'not yet available'
			print
			print 'Program Created by Eldara'
			rerun()
				

###Program Begins##
print 'Hello, Welcome to Infoscript, i am a basic program (The first of my masters) and i would like to thank you for using me'

print
print 'Would you like to lookup a user or add one?,'

start = raw_input('Type lookup or add:  ') # wait for the user #User inputs what they want

if start == 'add': #If they want to add a new user

	print

	name = raw_input("Type the first name: ")

	print

	lname = raw_input('Type the last name: ')

	print 

	age = raw_input('Type the age: ')

	print

	address = raw_input('What is his/her address ?  ')

	print

	Telephone = raw_input('Whats his/her telephone number ?  ')

	print

	print 'Ok, This is what you gave me'

	print

	print 'the name is', name, lname,
	print
	print 'they are ', age, 'years old',
	print
	print 'they live at', address, 
	print
	print 'And there number is', Telephone,

	print

	well = raw_input('is this ok?  ')

	if well == 'yes':
		print the
		print 'Storing Data Now'
		rerun() #rerun function from above
	else: 
		print
		print 'Why did you put it in wrong???? /n Well im a nice program so i wont save your mistake but now you have to start again'
	
		print 'Program Created by Eldara'
		rerun() #rerun function from above
			
								
else: #What happens if they try to lookup

	print 'not yet available'
	print
	print 'Program Created by Eldara'
	rerun()
	


```

If i take that line out it runs fine but it is needed or people cannot leave the script

Thanks in Advance,
Eldara

---

### Post by pointone on 2007-07-23
It's because you can't have two else statements in a row; once one is executed, the if / else block is finished, and Python thinks your second else is all alone (as in, without a matching if).

And while I'm here, you should use the "\n" (newline) character rather than all those extra print statements. For example, change:

```
				print

				print 'Ok, This is what you gave me'

				print
```

to:

```
print '\nOk, This is what you gave me\n'
```

---

### Post by Nekiruhs on 2007-07-23
Well.... First off, the first line is awful. its not #! user/bin/python. Its either #!/usr/bin/env python or #!/usr/bin/python. The first way is better because that always points to python, regardless. Your second, major error is a typo. you said raw_intput not raw_input. Use Eclipse IDE with PyDev addon, it corrects these errors.

---

### Post by eldara5 on 2007-07-24
Ye i know i should use /n but personally i think print looks neater XD, im starting to use /n more as it keeps the code less,

Thanks for the anwser

---

