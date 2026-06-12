---
title: "More noob Python"
date: 2009-07-13
forum: Programming Talk
---

### Post by crownedzero on 2009-07-13
This is what I'm working on.

[http://openbookproject.net/pybiblio/practice/wilson/loan.php](http://openbookproject.net/pybiblio/practice/wilson/loan.php)

Two things, first of all I am missing the '0' count, not a huge deal but it's not what was called for and so it isn't right. I've attempted changed the for statement to include (0, months) and the problem I ran into there is the "Remaining Balance" is all out of whack.

Second, again I do realize the long and short of it, but I know this coul've most like been done better. How and why?

My code:
```
#Loan calculator

print '''This is a simple loan calculator. Type 'quit'
to exit. It will attempt to calculate your payment schedule.
You will need to provide the amount borrowed, the interest
rate and the length of the loan. \n'''

   

#Define function to get the principal or amount borrowed
def get_principal():
    global principal
    
    running = True

    while running:
        principal = raw_input('Enter the amount borrowed: ')
        
        try:
            principal = float(principal)
            running = False

        except ValueError:
            if principal.lower() == 'quit':
                print 'Exiting'
                running = False

            else:
                print 'Please enter a valid amount'

#Define function to get the interest rate
def get_interest():
    global interest
    running = True

    while running:
        interest = raw_input('Enter the interest rate: ')

        try:
            interest = float(interest)
            running = False

        except ValueError:
            if interest.lower() == 'quit':
                print 'Exiting'
                running = False

            else:
                print 'Please enter a valid interest rate'

#Defines the function to get the lifetime of the loan, will later be converted into months
def get_term():
    global term
    running = True

    while running:
        term = raw_input('Enter the length of the loan in years: ')

        try:
            term = int(term)
            running = False

        except ValueError:
            if term.lower() == 'quit':
                print 'Exiting'
                running = False

            else:
                print 'Please enter a valid term'

get_principal()
get_interest()
get_term()

months = term * 12
total_paid = (principal * (interest * 0.01) + principal)
rem_balance = round(total_paid, 2)
payment = round((total_paid / months), 2)

print 'Amount borrowed: $%0.2f' % principal
print 'Interest rate: %0.2f%s' % (interest, '%')
print 'Term (years) :',term
print 'Number of payments :', months
print 'Total paid : %0.2f' % total_paid
print ''
print '             Amount      Remaining'
print 'Pymt#         Paid        Balance'
print '-----        ------      ---------'

for i in range (1, months + 1 ):
    rem_balance = round((rem_balance - payment), 2)
    if i == months:
        print i,'          $ %0.2f' % (total_paid -(payment * (months - 1))), '       $%0.2f' % 0
    elif i < 10:
        print i, '           $ %0.2f' % payment, '       $%0.2f' % rem_balance
    elif i > 10:
        print i, '          $ %0.2f' % payment, '       $%0.2f' % rem_balance
```

I'm learning so be gentle >.<

---

### Post by Can+~ on 2009-07-13
Well, aside from the use of a global (it's a short snippet so can be ignored), the one big fault I see is having this:

```

#Define function to get the principal or amount borrowed
def get_principal():
    global principal
    
[B]    running = True

    while running:
        principal = raw_input('Enter the amount borrowed: ')
        
        try:
            principal = float(principal)
            running = False

        except ValueError:
            if principal.lower() == 'quit':
                print 'Exiting'
                running = False

            else:
                print 'Please enter a valid amount'[/B]

#Define function to get the interest rate
def get_interest():
    global interest
[B]    running = True

    while running:
        interest = raw_input('Enter the interest rate: ')

        try:
            interest = float(interest)
            running = False

        except ValueError:
            if interest.lower() == 'quit':
                print 'Exiting'
                running = False

            else:
                print 'Please enter a valid interest rate'[/B]

#Defines the function to get the lifetime of the loan, will later be converted into months
def get_term():
    global term
[B]    running = True

    while running:
        term = raw_input('Enter the length of the loan in years: ')

        try:
            term = int(term)
            running = False

        except ValueError:
            if term.lower() == 'quit':
                print 'Exiting'
                running = False

            else:
                print 'Please enter a valid term'[/B]

get_principal()
get_interest()
get_term()

```

Three times a repetitive task, the only difference is on which variable they set, and in one the conversion is a float and in other an int.

Try to merge them all in a single function, I will post later my take on the problem.

---

### Post by Can+~ on 2009-07-13
Well.. never got a reply. It's the same as your original version, although every function done in a single one; passing the conversion function by reference as an argument.

This could be redone with a dictionary (using valuename to store it), but that's for you to try.

[PHP]#!/usr/bin/python

import sys

def user_request(conversion, valuename):
	value = 0
	
	while True:
		value = raw_input('Enter the %s:' % valuename)
		
		try:
			value = conversion(value)
			break
		except ValueError:
			if value.lower() == 'quit':
				print 'Exit'
				sys.exit(0)
			else:
				print 'Please enter a valid %s' % valuename
	
	return value

principal = user_request(float, "principal")
interest = user_request(float, "interest")
term = user_request(int, "term")

print "p",principal,"i",interest,"t",term
#do stuff here[/PHP]

---

### Post by crownedzero on 2009-07-14
Well, I'll have to be honest with you. Some of that is further ahead than what I am. This is my first week with any language so I'm just now starting to get the basics. I'll have to try your code and see it function and then break it down to see how it works. The biggest reason I called three different functions was mainly just to get more exposure to them.

---

### Post by crownedzero on 2009-07-14
I'm not sure exactly why you're calling the sys module. Outside of the function break out, is it serving another purpose? 

Am I correct in assuming that the value = 0 is setting all the variables to 0 prior to requesting user input?

I know the use of global is a "no-no" (so says the book, lol) but I was playing with multiple functions and needed a way to call them outside of their own function.

I'm pretty sure I'm following with the (conversion, valuename) variables but I'd definitely have to work with something like this before I was comfortable with it.

I greatly appreciate the input. Thanks again.

---

