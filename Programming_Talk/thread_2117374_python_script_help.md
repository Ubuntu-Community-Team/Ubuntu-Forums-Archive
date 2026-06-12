---
title: "python script help"
date: 2013-02-18
forum: Programming Talk
---

### Post by wingnut2626 on 2013-02-18
Hi guys.  Here is what i have.

```
from sys import exit

print "Welcome to My Month extractor.  What this does is take the number that you input between 1 and 12 and outputs the month.\nPress enter to continue."

raw_input()

def testing():
	which_one = raw_input("What month (1-12)? ")
	months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'Sepetember', 'October', 'November', 'December']
	[COLOR="DarkOrchid"]try:
	
		if 1 <= which_one <= 12:
			print "The month is", months[which_one - 1]

	except NameError :
		print "Undefined term or this is out of the range. Try another month (1-12)"
		testing()except NameError :
		print "Unde
	else:
		print "Try another month?  Y or N?"
		choice = raw_input(">")
		if choice == "N":
			print "Thank you for using my software."
			exit(0)
		if choice == "Y":
			print "Thanks for trying this again."
			testing()
	finally:
		pass[/COLOR]

testing()
```


My question is why doesnt the error handling block work?  This is the output that i get when i attempt to input a value out of the list 'months'.

```
Welcome to My Month extractor.  What this does is take the number that you input between 1 and 12 and outputs the month.
Press enter to continue.

What month (1-12)? afdasd
Try another month?  Y or N?
```


Thanks for your enlightenment.....

---

### Post by wingnut2626 on 2013-02-18
```
from sys import exit

print "Welcome to My Month extractor.  What this does is take the number that you input between 1 and 12 and outputs the month.\nPress enter to continue."

raw_input()

def testing():
	which_one = raw_input("What month (1-12)? ")
	months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'Sepetember', 'October', 'November', 'December']
	try:
	
		if 1 <= which_one <= 12:
			print "The month is", months[which_one - 1]

	except NameError :
		print "Undefined term or this is out of the range. Try another month (1-12)"
		testing()
	else:
		print "Try another month?  Y or N?"
		choice = raw_input(">")
		if choice == "N":
			print "Thank you for using my software."
			exit(0)
		if choice == "Y":
			print "Thanks for trying this again."
			testing()
	finally:
		pass

testing()
```



had to repost the code got jumbled

---

### Post by wingnut2626 on 2013-02-18
I think i may have figured it out.  Does it have to do with which_one being a raw_input variable?

---

### Post by The Cog on 2013-02-18
Yes. raw_input() returns a string. Since you want a number, you need to make a number from this string, like this perhaps:
```
month_number = int(which_one)
```
but this can raise a ValueError if the string doesn't look like an integer so you may want to catch that. I'm not sure if anything in your code can ever raise a NameError.

---

### Post by Tony Flury on 2013-02-18
I think the problem is two things : 

1) using raw_input will just give you back a string - which you then compare to some numbers - that is not a good idea - you need to use int to convert the input first. and as pointed out you get  a valueError if the string can't be convereted.
2) There is nothing in your try block which should generate an exception - and especially not a NameError. To do what you are trying to do you need to re-do your code and look for a different exception.

---

### Post by wingnut2626 on 2013-02-18
Thank you! Here is the revised code with the Value and variable conversion:



```
from sys import exit

print "Welcome to My Month extractor.  What this does is take the number that you input between 1 and 12 and outputs the month.\nPress enter to continue."

raw_input()

def testing():
	try:
		
		which_one = raw_input("What month (1-12)? ")
		months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'Sepetember', 'October', 'November', 'December']
	
	
		month_number = int(which_one)
		if 1 <= month_number <= 12:
			print "The month is", months[month_number - 1]
		else:
			print "The number is out of the range. Please pick another number between 1 and 12."
			testing()
	except ValueError:
		print "Non integer value detected.  Please pick between 1-12."
		testing()
	else:
		print "Try another month?  Y or N?"
		choice = raw_input(">")
		if choice == "N":
			print "Thank you for using my software."
			exit(0)
		if choice == "Y":
			print "Thanks for trying this again."
			testing()
	finally:
		pass

testing()
```

---

### Post by iMac71 on 2013-02-18
regarding to the months, you might use the following dictionary instead of your list; by this way each month could have its proper number instead of its number minus one:```
months={
1:'January',
2:'February',
3:'March',
4:'April',
5:'May',
6:'June',
7:'July',
8:'August',
9:'September',
10:'October',
11:'November',
12:'December'
}
```

---

### Post by Vaphell on 2013-02-18
... and with such a dictionary you would be able to test the input with
```
if( month_number in months ):
  print "The month is", months[month_number]
else:
  ...
```

---

