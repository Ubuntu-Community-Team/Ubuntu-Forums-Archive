---
title: "Fix python code to accept a float input"
date: 2009-05-21
forum: Programming Talk
---

### Post by aszxcv on 2009-05-21
I want to accept a float or int number then based on the number regardless of type give me the correct month and date . The code below only can accept int if i try to put a floating point number i get an error. 

```
#!/usr/bin/python 
#month in list 
month = [
	'January',
	'February',
	'March',
	'April',
	'May',
	'June',
	'July',
	'August',
	'September',
	'October',
	'November',
	'December']
# A list with one ending for each number from 1 to 31
ordinal = ['st', 'nd', 'rd'] + 17*['th']\
	+ ['st', 'nd', 'rd'] + 7*['th']\
        + ['st']
#get user input
monthnumber = raw_input ('What month were you born(1-12): ')
dates = raw_input ('What was the date when you born(1-31): ')
years = raw_input ('What year was it: ')

#convert string to int
monthtoint =  int(monthnumber)
datetoint = int(dates)
cleanmonth = month[monthtoint-1]

#date &ordinal 
nicedate = dates + ordinal[datetoint-1]+ ' '

#print out statement month date year
print 'you were born on ' +cleanmonth+ ' '+ nicedate + years
```

---

### Post by crdlb on 2009-05-21
I don't understand. There are no floats in your progam; do you mean that you want to accept an input like "4.0" and interpret it as the integer 4? If so, why? Aren't months, days, and years fundamentally whole numbers?

You could use a try block on the int(), catching ValueError, then trying int(float(string)), which should give you a truncated integer from a string containing a decimal point.

If I have misunderstood you, it would be helpful if you would pastebin the actual error traceback you get.

---

