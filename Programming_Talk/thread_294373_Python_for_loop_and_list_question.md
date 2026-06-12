---
title: "Python for loop and list question"
date: 2006-11-06
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-06
Hey all

A python question for you. If I have a list of variables like so 

```

var_a = 1
var_b = 2
var_c = 3

this_list=[var_a, var_b, var_c]

```

how could I use a for loop to get the variables name? Is this even possible. If it isn't I may run into problems. Any ideas guys (or gals for that matter :p )?

Thanks

Ironfistchamp

---

### Post by Tomosaur on 2006-11-06
You won't be able to list variable names unless you store them as strings within your code - the computer doesn't store variables as strings, it assigns a value to a memory address. There's no reason why you'd ever need to access variable names anyway, unless you have some very strange ideas about programming :P

---

### Post by ironfistchamp on 2006-11-06
Oh I do have some strange ideas :P. Basically I have a MySQL table that has some columns in it. The variable names correspond to the columns. I want to loop through the variables, check the value and if the value is what I want it to be then I add that and the name of the column into an query. Do you see what I mean. I guess I will have to have a think about this. Thanks for the reply

Ironfistchamp

---

### Post by Tomosaur on 2006-11-06
There are ways to achieve this, but you can't do it by variable names. You could make a dictionary (this is very easy to do in python, you should have a read up on it) or you could make different objects. I would suggest you make arrays represnting columns, then map each of these arrays to a string, or something similar. There are ways of doing it, just not how you thought :P

---

### Post by duff on 2006-11-06
Use a dictonary instead

```
my_vars = {
     'a':1,
     'b':2,
     'c':3
   }

for var,value in my_vars.iteritems():
   do_it(var, value)
```

---

### Post by ohgod on 2006-11-06
If you want an array that associates strings with values, then the dictionary object is for you.  It's an associative array, so when you add values to it you associate each value with a string.  Then you can retrieve that value using the string you assigned, rather than using an integer index like an array does.

Here's some info on dictionary objects in python:  
[http://docs.python.org/tut/node7.html#SECTION007500000000000000000]("http://docs.python.org/tut/node7.html#SECTION007500000000000000000")

---

### Post by ironfistchamp on 2006-11-06
Hehe thanks for the replies people. Here is how I solved it. May not be pretty but it came from my own head.

```

var_list = [name,addr1, addr2, town, city, postcode, telnum, dob, carer_name, carer_rel, emer_contact, med_history, medication, gp, social_worker, cpn, total_donations, other_services]
	var_names = ["name","addr1", "addr2", "town", "city", "postcode", "telnum", "dob", "carer_name", "carer_rel", "emer_contact", "med_history", "medication", "gp", "social_worker", "cpn", "total_donations", "other_services"]

	sql_stmt = 'select * from member where' 
	index = 0	
	for item in var_list:
		if item != "":
			if index == 0:
				sql_stmt += " "+var_names[index]+" = \""+item+"\""
			else:
				sql_stmt += " AND "+var_names[index]+" = \""+item+"\""
		
		index = index + 1


```

works perfectly for what I want.

Thanks

Ironfistchamp

---

