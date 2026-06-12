---
title: "Python Variables"
date: 2010-01-18
forum: Programming Talk
---

### Post by rsynv5 on 2010-01-18
Hi, I'm trying to make a simple program in Python to calculate a golfers handicap. How would i make it so a user could input their own variables, specifically the course rating and slope, for any golfers out there.

---

### Post by mattyB on 2010-01-18
Checkout Python's raw_input() function, this might be what you're looking for.

Example: raw_input() - [http://docs.python.org/library/functions.html#raw_input](http://docs.python.org/library/functions.html#raw_input)

your_var = raw_input("Enter something: ")
# type something in and press enter, this will cause the function to return your input
>> Enter something: 2+2
print "You entered " + your_var
>>You entered 2+2

Note raw_input is different from the input() function in that it won't evaluate Python expressions. If we applied the same example as above but to input(). Be forewarned however that the input() can throw an exception. Here's the Pydoc warning.

"This function is not safe from user errors! It expects a valid Python expression as input; if the input is not syntactically valid, a SyntaxError will be raised. Other exceptions may be raised if there is an error during evaluation. (On the other hand, sometimes this is exactly what you need when writing a quick script for expert use.)"


Example: input() - [http://docs.python.org/library/functions.html#input](http://docs.python.org/library/functions.html#input)

your_var = input("Enter something: ")
>> Enter something: 2+2
print "You entered " + your_var
>>You entered 4

Notice the expression 2+2 was evaluated and returned the number 4.

---

### Post by denarced on 2010-01-19
If you're just learning python(like it seems), it might wiser to check how things are done in python3. No radical changes from 2.6, but for example, there is no raw_input anymore

---

### Post by rsynv5 on 2010-01-19
I am currently using 3, so what would there be in addition to input()?

---

### Post by Can+~ on 2010-01-19
> **rsynv5 said:**
> I am currently using 3, so what would there be in addition to input()?

Python2.*:
raw_input : Returns a string
input : Returns actual python code (Known for being vulnerable)

Python3.*:
input : Returns a string

Accepting python code was a terrible idea, but I think they had that option for things like the command line interpreter, in which case, you can achieve the same thing with (python3):

[PHP]eval(input(" >>>"))[/PHP]

In your case, you won't have any problems, you'll probably want to convert from string to integer to work with arithmetic operations for your handicap tool:

[PHP]course_rating = int(input("Enter Course Rating: "))[/PHP]

Sample usage (I coded blindly, so there might be errors):

[PHP]#!/usr/bin/python3

# Request the course rating
course_rating = int(input("Enter Course Rating: "))

# Perform operation (dunno about golf)
course_rating *= 2

# Display result
print("Something something: {0}".format(course_rating))[/PHP]

---

### Post by OgreProgrammer on 2010-01-19
Hi rsynv5. I see you are using karmic?

Once you have the basics of python down, you could do your handicap program in glade with the quickly system. If you want to complicate it. The basic tutorial handles what you would need and you could store data in a database then.

sudo aptitude install quickly.

---

### Post by rsynv5 on 2010-01-21
Another quick question...
How do i print the value of a variable?

---

### Post by OgreProgrammer on 2010-01-21
> **rsynv5 said:**
> Another quick question...
How do i print the value of a variable?

print variable_name

---

### Post by rsynv5 on 2010-01-21
I've tried that. I get a syntax error.

---

### Post by epicoder on 2010-01-21
You're using python 3. 
```
print(your_var)
```

---

### Post by Can+~ on 2010-01-21
[http://docs.python.org/dev/3.0/whatsnew/3.0.html#print-is-a-function](http://docs.python.org/dev/3.0/whatsnew/3.0.html#print-is-a-function)

---

